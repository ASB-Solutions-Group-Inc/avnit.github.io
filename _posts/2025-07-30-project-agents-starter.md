---
layout: post
title: "Agents Starter"
subtitle: "Cloudflare's starter template for building AI chat agents on Workers"
gh-repo: avnit/agents-starter
gh-badge: [star, fork]
tags: [projects, ai-agents, web-dev, self-hosted]
comments: false
---

Agents Starter is Cloudflare's template for building AI chat agents on Workers, powered by their Agents SDK. It ships a working chat agent with streaming responses, tool use, scheduling, and vision — all running on Workers AI with no API key required. This is my fork, kept for experimenting with agent patterns on Cloudflare's edge.

## The concepts

What makes this template useful is that it demonstrates three distinct tool patterns in one place: server-side tools that auto-execute, client-side tools where the browser provides the answer (like timezone detection), and human-in-the-loop tools that ask for approval before running. On top of that it shows scheduling — one-time, delayed, and recurring cron tasks — plus a reasoning display that streams the model's thinking, image input for vision-capable models, and WebSocket-based real-time messaging with persistence. It is a compact tour of how the Agents SDK wires an LLM into a stateful, tool-using service.

## How to use it

The most impactful change is editing the `system` prompt in `server.ts` to give the agent its personality and focus. From there you replace the demo tools (a fake weather tool, a basic calculator) with real API calls, and add your own tools to the `tools` object following whichever of the three patterns fits.

## Running it

```bash
npx create-cloudflare@latest --template cloudflare/agents-starter
cd agents-starter
npm install
npm run dev
```

Open `localhost:5173` and try prompts like "What's the weather in Paris?" or "Remind me in 5 minutes to take a break" to exercise the different tool types.

**Language:** TypeScript
**Source code:** [github.com/avnit/agents-starter](https://github.com/avnit/agents-starter)
**Upstream:** [github.com/cloudflare/agents](https://github.com/cloudflare/agents/)
