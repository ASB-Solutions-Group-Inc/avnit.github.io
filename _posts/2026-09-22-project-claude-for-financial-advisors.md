---
layout: post
title: "Claude for Financial Advisors"
subtitle: "Anthropic's Claude Cowork plugin with ready-to-run workflows for financial advisors"
gh-repo: avnit/claude-for-financial-advisors
gh-badge: [star, fork]
tags: [projects, finance, ai-agents, learning]
comments: false
---

A plugin from Anthropic that gives financial advisors a set of ready-to-run workflows for Claude Cowork, drawing live data from the tools a firm already uses through third-party connectors. This is my fork of [anthropics/claude-for-financial-advisors](https://github.com/anthropics/claude-for-financial-advisors), kept as a reference for how to design agent workflows in a regulated field.

## The concepts

The plugin is a set of skills written as plain instructions in Markdown and JSON. Three design choices make it a good model to study:

- **It holds no client data.** When an advisor runs a skill, Claude pulls what it needs from the connected systems at that moment.
- **Writes need approval.** Any action that writes back to an external system — a CRM update, a client draft — pauses for the advisor to approve.
- **The division of labor is explicit.** Claude gathers, organizes, summarizes, and compares. The advisor exercises judgment and gives the advice.

## The skills

| Skill | What it does |
| :--- | :--- |
| `/onboarding` | Guided first-run setup that learns the firm, connects its tools, and runs a sample demo |
| `/pre-meeting` | Builds a client review prep document with open items, portfolio review, and an agenda |
| `/post-meeting` | Turns a meeting transcript into a CRM note |
| `/compliance` | Pre-checks client-facing material against the SEC Marketing Rule and Reg BI |
| `/prospect-intake` | Normalizes a prospect's statements into a summary and an analyst handoff |
| `/portfolio-rebalance-review` | Reviews performance and drift, and lays out tax-aware rebalance scenarios |
| `/alts-brief` | A meeting-ready read on a household's alternative investments |
| `/estate-and-tax-brief` | Cross-checks the estate plan against account titling and beneficiaries |

Each skill uses whichever connectors are live and falls back to paste or upload when a system isn't connected.

## A note on status

Upstream describes this as a reference implementation that is not actively maintained. It is educational and operational support for advisors, not investment, legal, or tax advice. Apache-2.0 licensed.

**Source code:** [github.com/avnit/claude-for-financial-advisors](https://github.com/avnit/claude-for-financial-advisors)  
**Upstream:** [github.com/anthropics/claude-for-financial-advisors](https://github.com/anthropics/claude-for-financial-advisors)
