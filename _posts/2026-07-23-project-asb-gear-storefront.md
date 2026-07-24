---
layout: post
title: "ASB Gear Storefront"
subtitle: "A zero-dependency e-commerce site with a deliberately payment-free checkout"
gh-repo: avnit/asb-gear-storefront
gh-badge: [star, fork]
tags: [projects, web-dev, e-commerce, security]
comments: false
---

**ASB Gear** is the hardware product line of ASB Solutions Group Inc., and this repo is its pre-launch storefront — a complete product-showcase site with a working cart and checkout, built with intentionally boring technology. Two products are in the catalogue: the **Nexus 9**, a 9-in-1 USB-C docking station, and the **DriveLink 15**, a 15W magnetic car charger mount.

## The concepts

Two deliberate design decisions shape this codebase:

**No stack.** Hand-written HTML, one CSS file (a full design system with light and dark modes), and two small JS files. No build step, no framework, no dependencies. It deploys to GitHub Pages, Cloudflare Pages, Netlify, S3, or an nginx container by copying the directory — a GitHub Actions workflow auto-deploys to Pages on every push.

**Reservations, not payments.** The checkout works end to end, but there are deliberately no card fields anywhere in the codebase. A checkout that collects card details with no processor behind it can't charge them and can't store them safely — it would just be a data-breach vector that drags the business into PCI-DSS scope for nothing. Instead, the flow goes cart → contact and shipping details → a pre-filled reservation email to sales → confirmation page, with customer-facing copy that says so at every step.

## How it's organized

Landing page, per-product detail pages with specs and FAQs, cart with quantity controls, checkout, confirmation, plus the policy pages (terms, privacy, returns with a 2-year warranty, shipping). Prices live in exactly one place — a `CATALOG` object in `cart.js`, stored in integer cents.

## Running and going live

Local preview is one command from the repo root:

```bash
python -m http.server 8080
```

To take real payments, the README documents the upgrade path: swap `submitReservation()` for Stripe Checkout, a Shopify Buy Button, or a merchant-of-record like Paddle — in every case the card fields live on the processor's hosted page, never in this codebase.

**Language:** HTML / CSS / JavaScript
**Source code:** [github.com/avnit/asb-gear-storefront](https://github.com/avnit/asb-gear-storefront)
