---
layout: post
title: "Auto Identity Remove"
subtitle: "Automated data-broker opt-outs on a monthly schedule"
gh-repo: avnit/auto-identity-remove
gh-badge: [star, fork]
tags: [projects, privacy, self-hosted, javascript]
comments: false
---

Auto Identity Remove is a cross-platform runner that scrubs your personal information off hundreds of people-search sites and data-broker databases automatically, once a month, so you don't have to file each opt-out by hand. This is my fork of [stephenlthorn/auto-identity-remove](https://github.com/stephenlthorn/auto-identity-remove), kept in my account for homelab use and study.

## The concepts

Data brokers aggregate your name, address, phone, and relatives into searchable profiles. Opting out of each one is tedious and has to be repeated, because listings reappear. This tool treats the problem as a scheduled job: it searches each broker for your name and state, finds your specific listing, fills and submits the opt-out form, and tracks persistent state so completed removals aren't resubmitted every run. CAPTCHA-protected forms are handled via CapSolver; anything that needs manual action gets opened in your browser.

Beyond the core run it can score your exposure on a 0-100 scale with a month-over-month trend, re-verify removals, watch search engines for new listings, and send CCPA/GDPR right-to-know requests. Personal info stays local: `config.json` and `state.json` are both gitignored and can be encrypted at rest.

## How to use it

The `aidr` CLI wraps everything. `aidr setup` runs interactive first-run configuration and schedules the monthly job, `aidr preview` dry-runs without submitting, and `aidr run` executes the real opt-out pass.

## Running it

```bash
git clone https://github.com/stephenlthorn/auto-identity-remove.git
cd auto-identity-remove
bash install.sh
./node_modules/.bin/aidr setup
```

It needs Node.js 18+ and a Playwright Chromium install (`npx playwright install chromium`).

**Language:** JavaScript
**Source code:** [github.com/avnit/auto-identity-remove](https://github.com/avnit/auto-identity-remove)
**Upstream:** [github.com/stephenlthorn/auto-identity-remove](https://github.com/stephenlthorn/auto-identity-remove)
