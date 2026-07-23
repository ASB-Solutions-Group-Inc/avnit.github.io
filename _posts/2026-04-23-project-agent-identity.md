---
layout: post
title: "Agent Identity"
subtitle: "A policy agent with per-agent identity on Vertex AI — no service-account keys"
gh-repo: avnit/agent-identity
gh-badge: [star, fork]
tags: [projects, ai-agents, google-cloud, security]
comments: false
---

An end-to-end reference implementation of a Google Agent Development Kit (ADK) agent that authenticates with a per-agent identity instead of a service-account key. I built it as a sample for a Customer Engineer offsite in Austin.

The agent answers questions about internal policy documents stored in Google Cloud Storage, and it can be registered as an add-on agent in Gemini Enterprise (formerly Agentspace).

## The concepts

The interesting part is the identity model. When the agent is deployed to Vertex AI Agent Engine with `identity_type = AGENT_IDENTITY`, it gets its own SPIFFE-style principal — IAM permissions are granted directly to that principal, not to a shared service account, and there is no JSON key to leak. Inside the agent, plain `google.auth.default()` resolves to the agent's identity at runtime.

A few other design points worth noting:

- **Tools are plain Python functions.** The ADK introspects type hints and docstrings to build the tool schema the model sees.
- **Gemini Enterprise is an add-on layer.** It doesn't host the agent — it registers a pointer to the Agent Engine deployment and surfaces it in the Gemini Enterprise UI.
- The model behind it is `gemini-2.5-flash` on Vertex AI.

## How to use it

The best entry point is the walkthrough notebook at `notebooks/policy_agent_walkthrough.ipynb`. It runs the whole flow end-to-end: environment check, install, bucket setup, local smoke test, deploy with Agent Identity, IAM bind, remote test, optional Gemini Enterprise registration, and teardown — with one configuration cell and copy-pasteable outputs at each step.

There are also standalone scripts: `local_run.py` for a local smoke test against your own ADC, `deploy.py` for the Agent Engine deployment, `remote_test.py` for hitting the live reasoning engine, and `register_gemini_enterprise.py` for the add-on registration.

## Running it

You need Python 3.10+, an authenticated `gcloud` (`gcloud auth application-default login`), and a billing-enabled project with Vertex AI and Storage roles. The repo is intentionally small — it's meant as a working starting point you can fork for your own policy or knowledge-base use cases.

**Language:** Jupyter Notebook / Python

**Source code:** [github.com/avnit/agent-identity](https://github.com/avnit/agent-identity)
