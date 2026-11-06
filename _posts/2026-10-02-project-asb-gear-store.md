---
layout: post
title: "ASB Gear Store"
subtitle: "A Django storefront and repair-ticket platform with real-time two-way eBay inventory sync"
gh-repo: avnit/asb-gear-store
gh-badge: [star, fork]
tags: [projects, python, web-dev, docker, self-hosted]
comments: false
---

The Django storefront and repair-ticket platform for ASB Gear Repair, with real-time two-way inventory sync to the ASB Solutions eBay store. It is a sibling to the earlier pre-launch [ASB Gear Storefront](https://github.com/avnit/asb-gear-storefront).

## The concepts

Selling the same physical unit in two places creates one hard problem: it must not sell twice. Most of the design follows from that.

- **One stock ledger, two channels.** Every quantity change is an append-only `StockLedger` row. A store checkout reserves the unit, and a worker pushes the reduced quantity to eBay so it can't sell there too.
- **Real-time sync with backstops.** Signed, deduplicated eBay platform notifications trigger an immediate re-read of the item. A five-minute delta poll and an hourly full sweep catch anything a missed push would have dropped.
- **A native shop.** eBay listings appear as first-class product pages with a rehosted photo gallery, sanitized descriptions, and a live stock badge. There are no links out to eBay.
- **Checkout that handles the race.** Stripe Checkout is off by default. If a unit sells on eBay mid-checkout, the reservation is revoked, and a late payment is refunded automatically.
- **Repair tickets.** Customer accounts, ticket tracking, private photo uploads, status history, and liability waivers.

The stack is Django 5.2 on MySQL 8, served by gunicorn behind nginx, and exposed through a Cloudflare Tunnel rather than an open inbound port.

## Running it

```bash
cd repair-app
python3 -m venv .venv && . .venv/bin/activate
pip install -r requirements.txt
export DEBUG=true
python manage.py migrate && python manage.py seed_catalog
python manage.py runserver     # http://127.0.0.1:8000/
python manage.py run_worker    # second terminal: the sync worker
```

For production, copy `.env.example` to `.env`, fill it in, and run `docker compose up -d --build`.

## Engineering notes

The repo keeps its reasoning next to its code: an intent document with the architecture, as-built notes, and a go-live runbook, plus a security scan document with audit findings and their remediation status. CI runs the tests on both SQLite and MySQL 8, runs Django's `check --deploy`, and builds the image.

**Language:** Python  
**Source code:** [github.com/avnit/asb-gear-store](https://github.com/avnit/asb-gear-store)
