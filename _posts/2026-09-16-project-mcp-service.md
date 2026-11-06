---
layout: post
title: "MCP Service"
subtitle: "An OpenAPI 3.1 service on Cloudflare Workers, built with Hono and chanfana"
gh-repo: avnit/mcp-service
gh-badge: [star, fork]
tags: [projects, typescript, serverless, web-dev]
comments: false
---

A small API service running on Cloudflare Workers, scaffolded from Cloudflare's OpenAPI 3.1 starter. What is in the repo today is the starting point — a task API with generated documentation — rather than a finished product.

## The concepts

The project combines two libraries:

- [Hono](https://github.com/honojs/hono) is the router.
- [chanfana](https://github.com/cloudflare/chanfana) generates the `openapi.json` schema from the code and validates each incoming request against the declared parameters and body.

The benefit is that the API contract cannot drift from the implementation, because the contract is derived from it. That matters for any service an AI agent will call: a tool definition is only as good as the schema behind it.

The router in `src/index.ts` registers four endpoints, each in its own file under `src/endpoints/`:

| Method | Path | Purpose |
| :--- | :--- | :--- |
| GET | `/api/tasks` | List tasks |
| POST | `/api/tasks` | Create a task |
| GET | `/api/tasks/:taskSlug` | Fetch one task |
| DELETE | `/api/tasks/:taskSlug` | Delete a task |

## Running it

From the `fragrant-breeze-84c7/` folder:

```bash
npm install
wrangler dev      # local instance with Swagger UI at http://localhost:8787/
wrangler deploy   # publish to Cloudflare Workers (after wrangler login)
```

Changes under `src/` reload automatically; refresh the Swagger page to see them.

**Language:** TypeScript  
**Source code:** [github.com/avnit/mcp-service](https://github.com/avnit/mcp-service)
