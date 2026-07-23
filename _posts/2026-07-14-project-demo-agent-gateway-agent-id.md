---
layout: post
title: "Agent Gateway + Agent Identity on Google Cloud"
subtitle: "Routing and authenticating AI agent traffic with federated identity"
gh-repo: avnit/demo-agent-gateway-agent-id
gh-badge: [star, fork, follow]
tags: [projects, python, gcp, security]
comments: false
---

A demo combining an agent gateway with agent identity concepts, showing how to route and authenticate AI agent traffic on Google Cloud — federated with Okta and Microsoft Entra ID (Azure AD), calling Gemini Enterprise.

Want to see it run first? The repository includes a self-contained, zero-setup Colab walkthrough of the entire flow — no GCP project required. See the `notebooks/` directory in the [source repo](https://github.com/avnit/demo-agent-gateway-agent-id).

## Three Security Questions for Agentic AI

This demo answers three critical security questions about agentic AI:

**1. Who is the agent?**
Every agent gets its own identity, not a shared key. Using dedicated service accounts plus Workload Identity Federation, each agent has a unique, verifiable identity tied to a service account in your GCP project.

**2. How does a human's identity reach the agent?**
Workforce Identity Federation brings your existing IdP users (Okta or Microsoft Entra ID) into Google Cloud without requiring GCP-specific passwords. The agent can then act on behalf of an authenticated human, inheriting their permissions and auditability.

**3. What can the agent do, and to what?**
The Agent Gateway brokers every Gemini Enterprise call, attaching the agent's cryptographic identity and enforcing IAM policies before the model is ever reached. This creates a policy enforcement layer between untrusted agent code and your LLM.

> **Note:** This is demo / reference code. Values are placeholders. Nothing here provisions live billing-bearing resources until you supply real IDs in `terraform.tfvars`. Review before running in any real project.

![Agent Identity Architecture Diagram](/assets/img/agent-identity-diagram.png)

## Architecture Overview

The diagram illustrates the complete identity flow for AI agents in a federated, zero-trust model.

**Left side — Enterprise Identity Providers:**

- **Okta** and **Microsoft Entra ID** (Azure AD) are your existing employee directories. They're the source of truth for who your humans are.

**Center — Federation Pools:**

- **Workforce Identity Federation Pool** is the bridge from your employees into Google Cloud. When your human (Alice) logs in with Okta or Entra, Google Cloud issues her a short-lived credential that proves "I am Alice, verified by Okta."
- **Workload Identity Federation Pool** does the same for machines. Your agent container gets a cryptographic identity proving "I am Agent-7, running on this exact VM, at this exact time."

**Right side — Google Cloud (Execution):**

- **Agent Identity (Service Account)** — Every agent has a dedicated GCP service account. This isn't a shared key; it's a unique principal that can be audited, revoked, and governed independently.
- **Agent Gateway** — The enforcement layer. Before your agent code even talks to Gemini Enterprise, the gateway intercepts the call, verifies the agent's identity, checks what policies allow, and either routes the request or denies it.
- **Gemini Enterprise** — The LLM stays behind policy. The agent never talks directly to it; the gateway is the only client.

## Why This Matters

- **Per-agent accountability**: Each agent is identifiable. You know which agent made each API call.
- **Human context**: The agent knows who invoked it (Alice), so it can honor her permissions and limitations.
- **Zero shared keys**: No API keys, no JWT secrets living in containers. Everything is ephemeral, cryptographically bound to the exact execution context.
- **Auditability**: Every step is loggable and verifiable in Google Cloud's Audit Logs.

If you're building agentic AI on Google Cloud, start with identity — everything else in the security model hangs off it.

**Language:** Jupyter Notebook  
**Source code:** [github.com/avnit/demo-agent-gateway-agent-id](https://github.com/avnit/demo-agent-gateway-agent-id)
