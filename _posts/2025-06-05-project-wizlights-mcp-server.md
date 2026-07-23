---
layout: post
title: "WiZ Lights MCP Server"
subtitle: "Letting an LLM control the smart lights via Model Context Protocol"
gh-repo: avnit/wizlights-mcp-server
gh-badge: [star, fork]
tags: [projects, python, iot, ai-agents, self-hosted]
comments: false
---

A Model Context Protocol (MCP) server that lets large language models control [WiZ](https://www.wizconnected.com/) smart lights. This is my fork of [jeettrivedi/wizlights-mcp-server](https://github.com/jeettrivedi/wizlights-mcp-server), kept in my account for use in my own smart-home and agent experiments.

## The concepts

MCP is the standard interface for giving LLMs tools, and this server is a nice, compact example of the pattern: it wraps the [pywizlight](https://github.com/sbidy/pywizlight) library, which speaks the local UDP protocol WiZ bulbs use, and exposes light control as MCP tools a model can call. Ask an assistant to dim the lights, and the model translates that into a tool call the server executes on the LAN — no cloud API in the middle.

Combined with the rest of my homelab (local Ollama inference, Home Assistant, n8n automations), a server like this is a building block for genuinely local AI home control.

## Running it

The project uses the `uv` package manager, with Node.js needed only for the MCP development server. To install it into Claude Desktop:

```bash
mcp install wizlights_mcp_server/server.py
```

And for development mode with live code mounting:

```bash
mcp dev server.py --with-editable .
```

MIT licensed.

**Language:** Python

**Source code:** [github.com/avnit/wizlights-mcp-server](https://github.com/avnit/wizlights-mcp-server)
**Upstream:** [github.com/jeettrivedi/wizlights-mcp-server](https://github.com/jeettrivedi/wizlights-mcp-server)
