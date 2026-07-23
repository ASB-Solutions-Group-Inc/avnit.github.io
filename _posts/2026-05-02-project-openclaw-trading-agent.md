---
layout: post
title: "OpenClaw Trading Agent"
subtitle: "An AI trading agent built on the Claude Agent SDK"
gh-repo: avnit/openclaw-trading-agent
gh-badge: [star, fork]
tags: [projects, ai-agents, trading]
comments: false
---

An AI trading agent for OpenClaw built with the Claude Agent SDK, covering the three pillars any trading automation needs: market data, portfolio management, and order execution. It's part of my ongoing experiments in running agentic trading workflows against real brokerage APIs — always in paper mode first.

## The concepts

The Claude Agent SDK gives an LLM a structured loop: it can call tools, observe results, and decide the next step rather than just generating text. Applied to trading, that means the agent can pull quotes and market context, reason about a position against portfolio state, and then propose or place an order through a broker interface — with each step visible and auditable.

Splitting the work into market data, portfolio management, and order execution keeps the risky part (execution) isolated behind its own boundary. That separation matters: an agent that can read the market freely should still hit a deliberate gate before anything touches an order.

## How it fits my setup

This connects to the broader trading automation I run in my homelab — n8n workflows against paper-trading accounts, with a Telegram command interface for oversight. The agent approach is the next iteration: instead of hand-wiring every decision path into a workflow, let the model reason within guardrails and keep humans in the approval loop for anything order-shaped.

The repo doesn't have a public README yet, so consider this a project marker rather than documentation — the interesting parts are still evolving.

**Source code:** [github.com/avnit/openclaw-trading-agent](https://github.com/avnit/openclaw-trading-agent)
