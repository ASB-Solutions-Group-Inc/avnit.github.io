---
layout: post
title: "StockSelector"
subtitle: "Picking securities on the principle of the Efficient Market Hypothesis"
gh-repo: avnit/StockSelector
gh-badge: [star, fork]
tags: [projects, groovy, learning]
comments: false
---

StockSelector is an early project that explores security selection through the lens of the Efficient Market Hypothesis (EMH) — the idea that you can only beat the market on the back of genuine research. It's meant to help find a security worth investing in based on market price, alpha, and beta, written in Groovy.

## The concepts

EMH holds that prices already reflect available information, so the program's framing is that any edge has to come from disciplined analysis rather than guesswork. To that end it looks at a security's market price alongside alpha (excess return over a benchmark) and beta (sensitivity to market movements), using those to reason about which securities are attractive. It's a study project from 2015, so it's best read as an exercise in turning a finance concept into code rather than as investment tooling.

## How to use it

You feed it the securities you're evaluating and let it score them on the price, alpha, and beta signals it computes, using the output as a research aid.

**Language:** Groovy  
**Source code:** [github.com/avnit/StockSelector](https://github.com/avnit/StockSelector)
