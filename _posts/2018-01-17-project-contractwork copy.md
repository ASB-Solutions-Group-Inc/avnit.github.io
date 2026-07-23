---
layout: post
title: "ContractWork"
subtitle: "Python Finance 101 class material — a stock beta calculator"
gh-repo: avnit/ContractWork
gh-badge: [star, fork]
tags: [projects, python, learning]
comments: false
---

ContractWork is class material from a Python Finance 101 exercise — a notebook that builds a stock beta calculator while learning machine learning with Python 3. It's an early hands-on project applying Python's data-analysis stack to a real financial concept: estimating how volatile a stock is relative to the market.

## The concepts

The notebook pulls a list of tickers from a CSV, adds a few reference instruments (Apple, Microsoft, the S&P 500), and downloads historical price data with pandas-datareader. From there the workflow is the classic finance-meets-Python one: use pandas and numpy to compute returns, then estimate each security's beta against a market benchmark. It leans on pandas, matplotlib, and numpy, so it doubles as a practical tour of that toolchain.

## How to use it

You open the notebook, edit the CSV of holdings to the stocks you care about, and re-run the cells to fetch prices and recompute betas. Because it fetches live market data, part of the exercise is handling the messiness of real symbols and missing values.

**Language:** Python  
**Source code:** [github.com/avnit/ContractWork](https://github.com/avnit/ContractWork)
