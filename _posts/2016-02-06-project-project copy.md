---
layout: post
title: "Sugar Trading Project (FINC 621)"
subtitle: "A quantitative sugar-vs-stocks trading strategy in R from grad school"
gh-repo: avnit/Project
gh-badge: [star, fork]
tags: [projects, r, finance, quant-trading]
comments: false
---

A quantitative trading project from my FINC 621 graduate finance course, built in R with teammates Evan, Hetal, and Preedee as team "Sugar Quant 40". The thesis: sugar prices and the stock prices of food and beverage companies are inversely related.

## The concepts

The strategy trades that inverse relationship — when sugar prices rise, short food and beverage stocks; when sugar falls, go long. Entries and exits are filtered through three technical indicators: the Relative Strength Index (RSI) for momentum and overbought/oversold conditions, the Commodity Channel Index (CCI) for price level relative to its average, and Bollinger Bands for volatility-based buy and sell thresholds. A daily sugar price change beyond set thresholds triggers the buy or sell indicators, and exits are defined at trade entry.

## How it's organized

The `R/` folder holds the pipeline: `Initialize.R` downloads the stock data and attaches indicators, `ProjectStart.R` creates the rules and generates trades, and `InSampleTesting.R` / `OutOfSampleTesting.R` are the entry points for backtesting each regime. `MonteCarlo.R` runs a Monte Carlo simulator over the results. There's even a bit of C++ — an Rcpp routine in `Src/` that merges Bloomberg sugar prices with the stock data. Input data (an XLK-based holdings list and Bloomberg sugar prices) lives in `Data/`.

## Running it

Load the project in R, run `Initialize.R` to pull stocks and indicators, then start from `InSampleTesting.R` or `OutOfSampleTesting.R` depending on which test you want.

This predates my cloud and AI career, but it's the same instinct — encode a hypothesis, backtest it, let the data judge — that today drives the paper-trading automation in my homelab.

**Language:** R

**Source code:** [github.com/avnit/Project](https://github.com/avnit/Project)
