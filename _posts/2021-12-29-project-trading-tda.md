---
layout: post
title: "Trading TDA"
subtitle: "A TD Ameritrade trading pipeline with BigQuery analytics and ARIMA forecasting"
gh-repo: ASB-Solutions-Group-Inc/trading-tda
gh-badge: [star, fork]
tags: [projects, python, trading, google-cloud, finance]
comments: false
---

**Trading TDA** is an early ASB Solutions Group trading application built against the TD Ameritrade API — a predecessor of my current IBKR/Alpaca automation stack. It pulls portfolio and market data through `tda-api`, lands it in Google BigQuery, and runs time-series forecasting over it.

## The concepts

The pipeline has three stages:

- **Authenticate and ingest** — OAuth against the TDA API (`authenticate.py`), then `import-portfolio.py` exports portfolio data as per-ticker CSVs
- **Warehouse** — the CSVs load into a BigQuery `trading.trading_data` table with `bq load --autodetect`, giving SQL analytics over the whole portfolio history
- **Forecast** — `arima.py` fits ARIMA models (via `statsmodels`) across the portfolio, with a debug mode and per-portfolio selection, plus `pandas_ta` and matplotlib for indicators and charts

## How to run it

Configuration lives in a local `setup.py` with the TDA API key, redirect URI, and a token path — the README is emphatic that the OAuth token file stays private. A startup script creates a virtualenv, sets `SETUPTOOLS_USE_DISTUTILS=stdlib` (needed at the time for the dependency chain), installs requirements, and assumes `gcloud` and `bq` are configured:

```bash
virtualenv my-venv && source my-venv/bin/activate
pip install -r Requirements.txt
python authenticate.py
python import-portfolio.py
python arima.py y ALL
```

Worth noting historically: the TD Ameritrade API this was built on has since been retired following the Schwab migration, so the repo stands as an archived snapshot of that era — the ideas (broker API → warehouse → forecast) carried forward into my later trading projects.

**Language:** Python
**Source code:** [github.com/ASB-Solutions-Group-Inc/trading-tda](https://github.com/ASB-Solutions-Group-Inc/trading-tda)
