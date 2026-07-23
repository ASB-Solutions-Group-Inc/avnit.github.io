---
layout: post
title: "Financial App"
subtitle: "Pulling market data with yfinance and charting it in Python"
gh-repo: avnit/financial-app
gh-badge: [star, fork]
tags: [projects, python, learning]
comments: false
---

A small Python project for pulling financial market data and charting it. It is a hands-on experiment in working with stock data programmatically rather than a polished application.

## The concepts

The core idea is straightforward: fetch historical price data for a ticker with the `yfinance` library, then visualize it with matplotlib. That pairing — `yfinance` for the data feed and matplotlib for the plot — is a common starting point for anyone exploring quantitative finance or building the first piece of a trading dashboard. The README sketches this as a short pipeline: import yfinance, get the data, and draw a chart.

## How I use it

This is a personal scratch project I used to get comfortable with the data-to-chart workflow — the same building blocks that show up when I tinker with market data and trading automation in my homelab. It stays intentionally minimal.

**Language:** Python
**Source code:** [github.com/avnit/financial-app](https://github.com/avnit/financial-app)
