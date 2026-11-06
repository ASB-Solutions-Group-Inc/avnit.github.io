---
layout: post
title: "TradingAgents"
subtitle: "A multi-agent LLM framework that mirrors how a trading firm reaches a decision"
gh-repo: avnit/TradingAgents
gh-badge: [star, fork]
tags: [projects, python, ai-agents, finance, trading]
comments: false
---

TradingAgents is a multi-agent trading framework in which specialized LLM agents play the roles found in a real trading firm and argue their way to a decision. This is my fork of [TauricResearch/TradingAgents](https://github.com/TauricResearch/TradingAgents), kept alongside my own trading-agent experiments as a reference for how to structure the debate.

## The concepts

A single prompt asking "should I buy this stock?" gives you one opinion with no pushback. TradingAgents splits the job into roles:

- **Analyst team** — fundamentals, sentiment, news, and technical analysts work in parallel, each with its own tools.
- **Researcher team** — a bullish and a bearish researcher debate the analysts' reports.
- **Trader** — turns the reports and the debate into a proposed trade, with timing and size.
- **Risk management and portfolio manager** — the risk team assesses the proposal and the portfolio manager approves or rejects it. Approved orders go to a simulated exchange.

What I find most useful to study is the care around backtesting honesty. Recent releases focus on point-in-time integrity — an analysis dated in the past only sees data that had been published by that date, and SEC EDGAR fundamentals are served as filed — which is the difference between a backtest and a hindsight story.

## How to use it

The framework ships a CLI and a Python package, runs in Docker, and supports a wide range of model providers, including OpenAI-compatible endpoints and local Ollama. It keeps a persistent decision log and can resume a run from a checkpoint. See the upstream README for installation and the API keys each data vendor needs.

The project is designed for research. It is not financial, investment, or trading advice, and results vary with the model, the period, and the data.

**Language:** Python  
**Source code:** [github.com/avnit/TradingAgents](https://github.com/avnit/TradingAgents)  
**Upstream:** [github.com/TauricResearch/TradingAgents](https://github.com/TauricResearch/TradingAgents)
