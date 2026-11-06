---
layout: post
title: "Antigravity ADK Examples"
subtitle: "Five progressively harder agents — from a single tool to a deployment on Agent Engine"
gh-repo: avnit/antigravity-adk-examples
gh-badge: [star, fork]
tags: [projects, python, ai-agents, google-cloud, learning]
comments: false
---

A self-teaching course for going from zero to shipping autonomous agents with Google's Antigravity IDE, the Agent Development Kit (ADK) 2.0, and Vertex AI Agent Engine. The examples were written by Hermes Agent for the Antigravity CLI, with me as the student: concepts first, then five working folders you can run as they are.

## The concepts

Three pieces fit together, and it helps to keep them separate:

| Piece | What it is | Where it runs |
| :--- | :--- | :--- |
| Antigravity | Google's agent-first IDE: you describe outcomes, agents plan, edit, run, and verify | Local desktop app |
| ADK 2.0 | Open-source framework for agents, tools, sessions, memory, and multi-agent graphs | `pip install google-adk` |
| Agent Engine | Managed runtime on Vertex AI that hosts ADK agents behind an HTTPS endpoint | Your GCP project |

The working model is: write the agent in ADK, iterate on it locally in Antigravity, then deploy it to Agent Engine.

## The five examples

1. **Hello Agent** (`ex1`) — one agent, one tool that returns the current time in any timezone.
2. **Multi-tool ReAct agent** (`ex2`) — web search plus a calculator, so you can watch the planner choose between tools.
3. **Multi-agent workflow** (`ex3`) — a Planner, a Coder, and a Reviewer composed behind a coordinator with `SequentialAgent`.
4. **Retrieval-augmented agent** (`ex4`) — answers grounded in a local folder of documents.
5. **Deploy to Agent Engine** (`ex5`) — takes an earlier agent and ships it to a managed endpoint with sessions and tracing, then calls it remotely.

## Running it

After the one-time setup in the README (a Python 3.11+ virtualenv, `gcloud auth application-default login`, and a `.env` copied from `.env.example`), every example runs the same way:

```bash
adk web        # dev UI at http://localhost:8000 — pick an example
adk run ex1    # or stay in the terminal
```

The README closes with Antigravity workflow tips and a list of common gotchas worth reading before you start.

**Language:** Python  
**Source code:** [github.com/avnit/antigravity-adk-examples](https://github.com/avnit/antigravity-adk-examples)
