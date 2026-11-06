---
layout: post
title: "Google Agent Skills"
subtitle: "Installable Agent Skills for Google Cloud and other Google products"
gh-repo: avnit/skills
gh-badge: [star, fork]
tags: [projects, google-cloud, ai-agents, learning]
comments: false
---

A collection of [Agent Skills](https://agentskills.io/home) for Google products and technologies, including Google Cloud. This is my fork of [google/skills](https://github.com/google/skills), kept as a reference for how Google structures skills and as a source for the ones I install.

## The concepts

A skill is a folder of instructions an AI coding agent loads only when a task calls for it. Instead of hoping the model remembers the right way to set up IAM or deploy to GKE, you give it a reviewed, versioned recipe. The collection is organized the way the work is:

- **Getting started** — authenticating to Google Cloud, onboarding, and a foundation builder.
- **Multi-product solutions** — a solution-architecture workflow, multi-agent security with Agent Gateway, building and deploying AI agents, hybrid search on AlloyDB, RAG on GKE, and a secure n-tier serverless web app.
- **AI/ML** — Agent Platform skills for inference, endpoint management, evaluation, alerting, and Model Garden deployment.

There is also a "skill finder" skill, which helps an agent locate the right skill for a task.

## How to use it

```bash
npx skills add google/skills
```

The installer asks which skills you want, which agents to configure, and whether to install for the project or globally. To update later, and optionally remove obsolete skills:

```bash
npx skills update
```

A skill is instructions your agent will follow with your credentials, so install from the upstream repository and read a skill before relying on it.

**Language:** Python  
**Source code:** [github.com/avnit/skills](https://github.com/avnit/skills)  
**Upstream:** [github.com/google/skills](https://github.com/google/skills)
