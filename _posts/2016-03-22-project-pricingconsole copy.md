---
layout: post
title: "Pricing Console"
subtitle: "An option price calculator in C# — binomial and Black-Scholes models"
gh-repo: avnit/PricingConsole
gh-badge: [star, fork]
tags: [projects, csharp, finance]
comments: false
---

A C# console application that prices American and European options. Per the README, it implements both binomial and Black-Scholes pricing models and maintains put-call parity — the no-arbitrage relationship that ties a call, a put, the underlying, and the risk-free rate together, and a good sanity check that a pricing implementation is internally consistent.

## The concepts

The two models cover the two classic approaches to option valuation. Black-Scholes gives a closed-form price for European options, which can only be exercised at expiry. The binomial model builds a discrete tree of possible underlying prices and steps backward through it, which is what makes it suitable for American options, where early exercise at any node has to be checked against continuation value. Keeping put-call parity intact across both is the discipline of the exercise.

This repo dates from 2016 — well before my current automated trading experiments — but it's an early data point in a long-running interest: the options pricing concepts here (Greeks, parity, model selection) are exactly what my newer trading tooling leans on, just with libraries doing the math now instead of hand-rolled C#.

## How to use it

It's a console app: build it with Visual Studio or the .NET toolchain of the era and run it from a terminal to price options against the implemented models.

**Language:** C#
**Source code:** [github.com/avnit/PricingConsole](https://github.com/avnit/PricingConsole)
