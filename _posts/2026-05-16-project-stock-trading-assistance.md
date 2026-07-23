---
layout: post
title: "Stock Trading Assistance (Argo)"
subtitle: "A research-to-proposal-to-approval loop for stocks and options, paper trading by default"
gh-repo: avnit/stock-trading-assistance
gh-badge: [star, fork]
tags: [projects, python, ai-agents, google-cloud, finance]
comments: false
---

Argo is my personal stock research and trading assistant: a full research → propose → human-approved-execute loop for both stocks and multi-leg options strategies. It is a personal-use research tool, paper trading only by default, and very deliberately not investment advice.

## The concepts

The same Python core is exposed three ways — a CLI (`argo ...`), a FastAPI HTTP API, and a React web UI. Under the hood it pulls 10-K sections and fundamentals from SEC EDGAR via `edgartools`, price history and option chains from `yfinance`, computes Black-Scholes Greeks with `py_vollib_vectorized`, and estimates probability of profit and breakevens with `optionlab`. A built-in strategy selector matches thesis direction against the IV regime to pick one of seven templates (long call/put, spreads, iron condor, covered call, cash-secured put), Claude writes a one-page thesis, and `alpaca-py` handles paper execution. SQLite keeps the research, tickets, and execution audit log.

## Guardrails

This is the part I care most about: paper trading by default, a hard $500-per-trade notional cap re-checked at execution time (applied against max loss for options), a typed-confirmation execute step, and an `argo halt` command that cancels all open orders and blocks pending tickets.

## Running it

```bash
uv venv && source .venv/bin/activate
uv pip install -e ".[dev,server]"
argo research NVDA
argo propose-options NVDA
argo execute TKT-001 --confirm
```

The repo also ships a `cloudbuild.yaml` and multi-stage Dockerfile that bundle the React SPA into the FastAPI image and deploy to Google Cloud Run, with API keys held in Secret Manager.

**Language:** Python
**Source code:** [github.com/avnit/stock-trading-assistance](https://github.com/avnit/stock-trading-assistance)
