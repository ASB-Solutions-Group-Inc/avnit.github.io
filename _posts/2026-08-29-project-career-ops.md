---
layout: post
title: "career-ops"
subtitle: "An open-source, local-first AI job search that helps you apply better to fewer roles"
gh-repo: avnit/career-ops
gh-badge: [star, fork]
tags: [projects, javascript, ai-agents, open-source]
comments: false
---

career-ops is an open-source AI job-search system that runs locally inside an AI coding CLI such as Claude Code, Codex, OpenCode, or Antigravity. It scans job portals, evaluates each listing into a structured report with a global 1–5 score, tailors your CV, and tracks your applications. This is my fork of [career-ops-hq/career-ops](https://github.com/career-ops-hq/career-ops), kept as a study in how to package a real workflow as agent skills.

## The concepts

Companies use AI to filter candidates; this project gives the candidate a filter of their own. The README sums up its practice in a handful of short principles: send fewer, better applications; prefer signal to volume and evidence to keywords; keep a human in charge; keep the data local.

Two of those are design decisions I'd point to in any agent project:

- **A human decides.** The tool tells you whether a job is still open and whether it fits, tailors the CV, and drafts your answers. You press Submit. It does not mass-apply on your behalf.
- **Local-first.** Your CV and your application history stay on your machine, inside the CLI you already use.

A "do not apply" result is treated as a good outcome: it gives you the evening back.

## How to use it

```bash
npx @santifer/career-ops init
```

Then paste a job you were about to apply to and read the evaluation. See the upstream README and [career-ops.org](https://career-ops.org) for the supported CLIs and the full workflow. MIT licensed.

**Language:** JavaScript  
**Source code:** [github.com/avnit/career-ops](https://github.com/avnit/career-ops)  
**Upstream:** [github.com/career-ops-hq/career-ops](https://github.com/career-ops-hq/career-ops)
