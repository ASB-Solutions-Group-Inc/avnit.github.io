---
layout: post
title: "ADK Samples"
subtitle: "Sample security agents built on Google's Agent Development Kit"
gh-repo: avnit/adk-samples
gh-badge: [star, fork]
tags: [projects, ai-agents, google-cloud, security]
comments: false
---

ADK Samples is a collection of ready-to-use agents built on Google's Agent Development Kit (ADK). My fork focuses on the security-oriented samples — fact-checking LLM output, retrieval-augmented generation, and cloud-security integration — which line up directly with my work as an AI and security specialist at Google Cloud.

## The concepts

The repository shows a spread of agent complexity, from a single-purpose auditor to multi-agent workflows. Three samples stand out. The **LLM Auditor** is an automated fact-checking layer: it identifies factual claims in a model's response, verifies them with Google Search and internal knowledge, and can rewrite the answer to correct inaccuracies. The **RAG agent** answers questions about documents uploaded to Vertex AI RAG Engine and returns answers with citations back to the source. The **Wiz MCP server** exposes the Wiz cloud-security platform as a Model Context Protocol server, so an AI assistant can query cloud-security findings through a standard interface.

## How to use it

Each agent lives in its own directory under `python/agents/` with a dedicated README covering setup and configuration. You pick the sample you want, install its dependencies with Poetry, supply the relevant Google Cloud and agent-specific credentials, and run it through the ADK CLI or web interface.

## Running it

```bash
git clone https://github.com/google/adk-samples.git
cd adk-samples/python
```

You need Python 3.9+, Poetry, and a Google Cloud account for most agents. These samples are for demonstration rather than production use.

**Language:** Python
**Source code:** [github.com/avnit/adk-samples](https://github.com/avnit/adk-samples)
**Upstream:** [github.com/google/adk-samples](https://github.com/google/adk-samples)
