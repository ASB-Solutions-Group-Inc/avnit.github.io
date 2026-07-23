---
layout: post
title: "Option Pricing"
subtitle: "An early web-based option price calculator"
gh-repo: avnit/optionPricing
gh-badge: [star, fork]
tags: [projects, web-dev, trading, learning]
comments: false
---

An option price calculator from 2016 — an early web project implementing options pricing with a browser front end, from back when my interest in trading tooling was just getting started.

## The idea

Option pricing is one of those problems that rewards building it yourself. Models like Black-Scholes take a handful of inputs — spot price, strike, time to expiry, volatility, interest rate — and produce a theoretical price, and wiring that into a web page forces you to actually understand what each input does to the result. A calculator you built is a much better teacher than one you found.

## Where it led

This repo is nearly a decade old now and shows its age (the primary language GitHub detects is CSS, which tells you it's front-end-heavy and from a simpler era of web development). But the through-line is real: the same interest in pricing and markets that produced this little calculator eventually grew into the automated trading experiments I run today — wheel strategies, credit spreads, and an AI trading agent, all against paper accounts in the homelab. Everyone's got a first repo on a topic; this was mine for trading.

**Language:** CSS  
**Source code:** [github.com/avnit/optionPricing](https://github.com/avnit/optionPricing)
