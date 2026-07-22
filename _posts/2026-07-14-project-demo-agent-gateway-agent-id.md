---
layout: post
title: demo-agent-gateway-agent-id
subtitle: Agent gateway + agent identity demo
gh-repo: avnit/demo-agent-gateway-agent-id
gh-badge: [star, fork, follow]
tags: [projects, python]
comments: false
---

A demo combining an agent gateway with agent identity concepts, showing how to route and authenticate AI agent traffic on Google Cloud.

demo-agent-gateway-agent-id
Agent Gateway + Agent Identity on Google Cloud — federated with Okta and Microsoft Entra ID (Azure AD), calling Gemini Enterprise.

Open In Colab

This demo shows how an AI agent running on Google Cloud obtains a verifiable, short-lived identity that is federated from your existing enterprise IdP (Okta or Entra ID), and uses that identity to call Gemini Enterprise through an Agent Gateway that enforces per-agent authorization.

🚀 Want to see it run first? Click the Open in Colab badge above for a self-contained, zero-setup walkthrough of the entire flow — no GCP project required. See notebooks/.

It answers three questions security architects ask about agentic AI:

***Who is the agent?*** 
    — Every agent gets its own identity, not a shared key. (Agent Identity / dedicated service accounts + Workload Identity Federation.)
*** How does a human's identity reach the agent? ***
    — Workforce Identity Federation brings Okta / Entra ID users into GCP without minting GCP passwords, so the agent can act on-behalf-of an authenticated human.
*** What can the agent do, and to what? *** 
    —  The Agent Gateway brokers every Gemini Enterprise call, attaches the agent's identity, and enforces IAM + policy before the model is ever reached.
⚠️ Demo / reference code. Values are placeholders. Nothing here provisions live billing-bearing resources until you supply real IDs in terraform.tfvars. Review before running in any real project.

![Agent Identity Architecture Diagram](/assets/img/agent-identity-diagram.png)

**Language:** Jupyter Notebook  
**Source code:** [github.com/avnit/demo-agent-gateway-agent-id](https://github.com/avnit/demo-agent-gateway-agent-id)
