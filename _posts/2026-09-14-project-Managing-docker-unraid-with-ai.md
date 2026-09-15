---

# Managing Unraid & Docker with AI Agents: Integrating an Unraid MCP Server with Claude Code and Hermes Agent

**Author**: Avnit Bambah

**Date**: September 14, 2026

**Category**: Homelab, AI Systems & Automation


---

### Introduction

Managing a dense homelab server often means navigating between disparate web interfaces, SSH sessions, and log tailing utilities. On a typical Unraid storage server running dozens of containerized services—media stacks (*arr, Jellyfin), document indexing (Paperless-ngx), databases, and network utilities—triaging a stalled container or monitoring a monthly array parity check typically requires manual intervention.

With the advent of the **Model Context Protocol (MCP)**, we can give AI agents structured, tool-based access to our infrastructure without opening insecure root shells or hardcoding administrative credentials.

This post details how to build and deploy an **Unraid MCP Server** and connect it to two complementary agent environments:

1. **Claude Code**: For direct terminal-driven infrastructure management, refactoring container configs, and local CLI triage.
2. **Hermes Agent**: For persistent background monitoring, local LLM execution via Ollama, and remote operational triage over Telegram or Discord.

---

### Architecture Overview

The MCP server sits between your AI client and Unraid’s management APIs, translating high-level model tool calls into scoped API requests or Docker engine commands.

```
┌───────────────────────────────────────┐      ┌───────────────────────────────────────┐
│              Claude Code              │      │       Hermes Agent (Nous Research)    │
│       (Local Workstation / CLI)       │      │   (Debian VM / Telegram & Discord)    │
└───────────────────┬───────────────────┘      └───────────────────┬───────────────────┘
                    │                                              │
                    │               Model Context Protocol         │
                    └───────────────────────┬──────────────────────┘
                                            ▼
                        ┌───────────────────────────────────────┐
                        │           Unraid MCP Server           │
                        │      (FastMCP / Python Container)     │
                        └───────────────────┬───────────────────┘
                                            │
                    ┌───────────────────────┴───────────────────────┐
                    ▼                                               ▼
         [Unraid GraphQL API]                            [Docker Daemon / Engine]
   (Array status, disks, parity)                  (Containers, lifecycle, log stream)

```

Communication with Unraid is handled via two primary interfaces:

* **Unraid Connect GraphQL API (`unraid-api`)**: Used for array health, storage pool metrics, parity check status, and system telemetry.
* **Docker Socket / Engine API (`/var/run/docker.sock`)**: Used for container inventory, inspection, lifecycle actions (`start`, `stop`, `restart`), and trailing log capture.

---

### Step 1: Provisioning Scoped Unraid Credentials

To adhere to least-privilege security principles, avoid passing your Unraid root password to the MCP server. Instead, create a scoped API key using the built-in `unraid-api` CLI:

```bash
#!/usr/bin/env bash
# Run on your Unraid host (e.g. via SSH or web terminal)
set -euo pipefail

# Ensure Unraid API service is active
unraid-api status || unraid-api start

# Generate a scoped API key for the MCP agent
unraid-api apikey --create --name mcp-agent --roles viewer

```

For container operations, mount the Docker socket in read-only mode (`/var/run/docker.sock:ro`) for monitoring agents, or read-write only if you explicitly enable container lifecycle management.

---

### Step 2: The MCP Server Toolset

Implemented using Python and the `FastMCP` framework, the server exposes discrete, typed tools to the agent:

```python
"""unraid_mcp_server.py - FastMCP Server for Unraid and Docker Management"""

import os
import docker
import requests
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("unraid-manager")
docker_client = docker.from_env()

UNRAID_HOST = os.getenv("UNRAID_HOST", "http://192.168.0.95")
UNRAID_API_KEY = os.getenv("UNRAID_API_KEY", "")

@mcp.tool()
def unraid_get_array_status() -> dict:
    """Returns the current Unraid array status, disk health, and parity check progress."""
    query = """
    query {
      array {
        state
        capacity { bytes { total used free } }
        parities { id status temp size }
        disks { id name status temp size }
      }
    }
    """
    headers = {"x-api-key": UNRAID_API_KEY, "Content-Type": "application/json"}
    resp = requests.post(f"{UNRAID_HOST}/graphql", json={"query": query}, headers=headers, timeout=10)
    return resp.json().get("data", {}).get("array", {})

@mcp.tool()
def unraid_list_containers(all: bool = True) -> list[dict]:
    """Lists all Docker containers on Unraid, including status, image, and port mappings."""
    containers = docker_client.containers.list(all=all)
    return [
        {
            "name": c.name,
            "status": c.status,
            "image": c.image.tags[0] if c.image.tags else c.short_id,
            "ports": c.ports,
        }
        for c in containers
    ]

@mcp.tool()
def unraid_get_container_logs(container_name: str, tail: int = 50) -> str:
    """Fetches trailing logs from a specific container for fault diagnosis."""
    try:
        container = docker_client.containers.get(container_name)
        return container.logs(tail=tail).decode("utf-8", errors="replace")
    except docker.errors.NotFound:
        return f"Error: Container '{container_name}' not found."

@mcp.tool()
def unraid_manage_container(container_name: str, action: str, confirm: bool = False) -> str:
    """
    Executes a lifecycle action ('restart', 'start', 'stop') on a container.
    Requires confirm=True for safety.
    """
    if not confirm:
        return f"Confirmation required to execute '{action}' on '{container_name}'. Pass confirm=True."

    if action not in ["start", "stop", "restart"]:
        return f"Unsupported action: '{action}'. Allowed: start, stop, restart."

    try:
        container = docker_client.containers.get(container_name)
        getattr(container, action)()
        return f"Successfully executed '{action}' on container '{container_name}'."
    except Exception as e:
        return f"Failed to execute '{action}': {str(e)}"

if __name__ == "__main__":
    mcp.run()

```

---

### Step 3: Integrating with Claude Code

**Claude Code** natively supports MCP servers via its configuration file or CLI flags.

#### 1. Configuration

Add the Unraid server to your Claude Code MCP configuration (`~/.claude.json` or project-level configuration):

```json
{
  "mcpServers": {
    "unraid": {
      "command": "python",
      "args": ["/opt/mcp-servers/unraid_mcp_server.py"],
      "env": {
        "UNRAID_HOST": "https://192.168.0.95",
        "UNRAID_API_KEY": "YOUR_UNRAID_API_KEY"
      }
    }
  }
}

```

#### 2. Usage in Terminal

Once configured, launch Claude Code in your terminal:

```bash
claude

```

You can now issue natural-language operational prompts directly:

```text
> Check the health of my Unraid array and list any stopped Docker containers.

```

**Claude Code Execution**:

1. Invokes `unraid_get_array_status` to verify disk temps and parity state.
2. Invokes `unraid_list_containers(all=True)` to filter containers where `status != "running"`.
3. Synthesizes a structured markdown table detailing system status and highlighting stopped services.

---

### Step 4: Integrating with Hermes Agent (Nous Research)

While Claude Code excels at interactive developer sessions, **Hermes Agent** operates effectively as an autonomous, persistent homelab assistant connected to local models (via Ollama) or cloud providers, with messaging bots on Telegram and Discord.

#### 1. Configuration in `~/.hermes/config.yaml`

Register the MCP server in your Hermes configuration:

```yaml
model:
  provider: "ollama"
  default: "qwen3-coder:30b"   # Or "anthropic" / "claude-sonnet-4-6"

mcp_servers:
  unraid:
    command: "python"
    args: ["/opt/mcp-servers/unraid_mcp_server.py"]
    env:
      UNRAID_HOST: "https://192.168.0.95",
      UNRAID_API_KEY: "YOUR_UNRAID_API_KEY"

gateway:
  telegram:
    enabled: true
    token: "${TELEGRAM_BOT_TOKEN}"
    allowed_users: ["your_telegram_handle"]

```

#### 2. Mobile Triage via Telegram

With the Telegram gateway active, you can monitor and manage your server on the go:

> **You (Telegram)**: *"Why is Paperless-ngx throwing 500 errors on Unraid?"*
> **Hermes Agent**:
> 1. Calls `unraid_get_container_logs(container_name='paperless-ngx', tail=30)`.
> 2. Detects: `redis.exceptions.ConnectionError: Error connecting to 192.168.0.17:6379`.
> 3. Identifies the root cause: The external Valkey/Redis cache host (`192.168.0.17`) is unreachable or bound to `127.0.0.1` rather than `0.0.0.0`.
> 4. Replies with a concise diagnostic summary and remediation instructions.
> 
> 

---

### Practical Use Cases

| Scenario | Agent Workflow | Tools Invoked |
| --- | --- | --- |
| **Parity Check Verification** | Monitors sync speed, errors, and disk temperatures. | `unraid_get_array_status` |
| **Crashing Container Triage** | Identifies failed state, extracts error stack trace, pinpoints missing mounts or port conflicts. | `unraid_list_containers`, `unraid_get_container_logs` |
| **Safe Lifecycle Actions** | Restarts or stops containers while enforcing human-in-the-loop confirmation gates. | `unraid_manage_container` |

---

### Safety Rules & Operational Lessons

1. **Explicit Confirmation Gates**: Destructive operations (`stop`, `restart`, array maintenance) must require an explicit `confirm=True` parameter so the model cannot trigger unprompted restarts.
2. **Read-Only Separation**: For public or autonomous chat gateways, expose only read-only query tools (`unraid_get_array_status`, `unraid_list_containers`, `unraid_get_container_logs`).
3. **Storage Awareness**: When diagnosing container failures, check underlying mount paths. SQLite databases mapped to network shares (e.g. NFS) are prone to locking issues and should always reside on local cache NVMe storage (`/mnt/cache/appdata/`).

---

### Conclusion

Integrating Unraid with an MCP server transforms homelab management from manual dashboard checking into an intuitive, agent-driven workflow. Whether you use Claude Code for terminal-driven development or Hermes Agent for conversational mobile triage, MCP provides a safe, standard interface to interact with your server hardware and container stacks.

For reference implementations, Docker Compose deployment templates, and multi-node Proxmox integration, explore the [github.com/avnit/mcp-proxmox-unraid-agent](https://www.google.com/search?q=https://github.com/avnit/mcp-proxmox-unraid-agent) repository.
