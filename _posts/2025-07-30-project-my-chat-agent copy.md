---
layout: post
title: "My Chat Agent"
subtitle: "An AI chat agent on Cloudflare Workers, built from the agents starter kit"
gh-repo: avnit/my-chat-agent
gh-badge: [star, fork]
tags: [projects, typescript, ai-agents, web-dev]
comments: false
---

A TypeScript chat agent running on Cloudflare's Agent platform, built from Cloudflare's [agents-starter](https://github.com/cloudflare/agents-starter) template. I used it to explore what serverless, edge-deployed AI agents look like in practice.

## The concepts

The starter is built on the [`agents`](https://www.npmjs.com/package/agents) package and gives you a full working loop out of the box: an interactive chat UI with real-time streaming responses, state management with chat history, and a tool system with human-in-the-loop confirmation. Tools defined *with* an `execute` function run automatically; tools defined *without* one pause and wait for the user to confirm before an execution handler runs — a pattern I care about a lot, since unconfirmed tool execution is where agent deployments get risky.

It also ships task scheduling (one-time, delayed, and recurring via cron), which turns a chat agent into something that can act later, not just respond now.

## How to use it

The code splits cleanly: `src/server.ts` holds the agent logic, `src/tools.ts` the tool definitions, and `src/app.tsx` the chat UI. The model provider is pluggable through the Vercel AI SDK — the template defaults to OpenAI, but it can be swapped for Workers AI or Anthropic providers.

## Running it

```bash
npm install
# put OPENAI_API_KEY in .dev.vars
npm start        # local dev
npm run deploy   # deploy to Cloudflare
```

You need a Cloudflare account and an API key for whichever model provider you wire in.

**Language:** TypeScript

**Source code:** [github.com/avnit/my-chat-agent](https://github.com/avnit/my-chat-agent)
