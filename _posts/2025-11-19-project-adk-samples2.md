---
layout: post
title: "ADK Samples"
subtitle: "Ready-to-use agents built on Google's Agent Development Kit"
gh-repo: avnit/adk-samples2
gh-badge: [star, fork]
tags: [projects, python, ai-agents, google-cloud]
comments: false
---

A working collection of ready-to-use agents built on Google's [Agent Development Kit (ADK)](https://google.github.io/adk-docs/), the framework for building AI agents that range from simple conversational bots to complex multi-agent workflows. I keep this alongside my other Google Cloud AI experiments to have real, runnable agent code on hand.

## The concepts

The repo is a catalogue of sample agents across common use cases and complexity levels. The Python side includes agents for academic research, brand search optimization, customer service, data science, a financial advisor, FOMC research, an LLM auditor, a marketing agency, personalized shopping, RAG, and a travel concierge. There's a Java side too, with a software bug assistant and time-series forecasting. Each one demonstrates ADK patterns you can lift into your own agents rather than starting from a blank file.

## How to use it

You pick the agent closest to what you're building, read its folder-level setup instructions, and run it against your own Google Cloud project and models. The samples are meant for demonstration and learning — Google is explicit that they aren't production-supported — so they're best treated as a pattern library.

## Running it

Navigate into the `python/` or `java/` subfolder and follow that language's setup steps to install dependencies and configure credentials, then launch the agent you want to try.

**Language:** Python  
**Source code:** [github.com/avnit/adk-samples2](https://github.com/avnit/adk-samples2)
