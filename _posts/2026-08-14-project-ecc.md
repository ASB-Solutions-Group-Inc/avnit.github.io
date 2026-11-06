---
layout: post
title: "ECC"
subtitle: "An agent harness system — skills, agents, hooks, memory, and security scanning for coding agents"
gh-repo: avnit/ECC
gh-badge: [star, fork]
tags: [projects, javascript, ai-agents, security, learning]
comments: false
---

ECC describes itself as an agent harness performance optimization system: a large, installable collection of skills, specialized agents, hooks, rules, and memory for AI coding agents. This is my fork of [affaan-m/ECC](https://github.com/affaan-m/ECC), kept as a reference while I build my own skills and agent workflows.

## The concepts

The idea is that a good engineering loop should not have to be re-explained in every prompt:

```text
plan -> test -> implement -> review -> verify -> remember -> improve
```

You install the process once and it becomes part of how the agent works. The project's own summary is "optimize the context window, persist everything else." What ships in the box:

| Included | What it gives you |
| :--- | :--- |
| 71 agents | Planning, review, build repair, security, architecture, and domain work |
| 311 skills | TDD, research, security, docs, frontend, data, ML, operations, and more |
| Hooks and memory | Enforcement, session summaries, continuous learning, and context controls |
| Rules | Always-loaded standards you choose by language or project |
| AgentShield | Scanning of prompts, hooks, MCP config, permissions, secrets, and agent files |

It works best with Claude Code, has native plugin paths for Codex and Qoder, and provides more limited adapters for Cursor, OpenCode, Gemini, Antigravity, and other harnesses.

## How to use it

Upstream recommends the guided setup, which needs Node.js 18 or newer:

```bash
npx ecc-universal@2.2.3 setup
```

One caution from the upstream README that is worth repeating: install only from the official channels (the upstream GitHub repo, the `ecc-universal` npm package, or [ecc.tools](https://ecc.tools)). An agent harness runs with your permissions, so an unofficial mirror is a real supply-chain risk. My fork is for reading, not a distribution channel.

**Language:** JavaScript  
**Source code:** [github.com/avnit/ECC](https://github.com/avnit/ECC)  
**Upstream:** [github.com/affaan-m/ECC](https://github.com/affaan-m/ECC)
