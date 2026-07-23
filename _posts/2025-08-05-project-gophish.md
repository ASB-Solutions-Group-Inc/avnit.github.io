---
layout: post
title: "Gophish"
subtitle: "An open-source phishing toolkit for security awareness programs"
gh-repo: avnit/gophish
gh-badge: [star, fork]
tags: [projects, security, self-hosted]
comments: false
---

Gophish is an open-source phishing toolkit built for businesses and penetration testers to run authorized phishing simulations and security awareness training. This is my fork of the [Evilginx-compatible build](https://github.com/kgretzky/gophish) — a variant of the [original Gophish](https://github.com/gophish/gophish) modified to work alongside the Evilginx framework. As a security professional, I keep it for studying how these tools fit into sanctioned assessment workflows.

## The concepts

Gophish exists so that defenders can measure and improve human resilience to phishing under controlled, consent-based conditions. You define target groups, email templates, and landing pages, then launch a campaign and watch the results dashboard: who opened the email, who clicked, and who submitted data. Those metrics feed awareness training and let an organization track improvement over time. The Evilginx-compatible fork extends this toward simulating session-token capture, which is relevant when testing how well an organization's MFA and detection controls hold up — strictly within an authorized engagement.

## How to use it

In practice this is a tool for red teams and awareness programs operating with written authorization. It is not something to point at anyone without explicit permission — the value is in realistic, sanctioned simulations that produce training data, not in the mechanics of any individual attack.

## Running it

Gophish ships as a single binary for Windows, macOS, and Linux, and there's an official Docker image. See the upstream documentation for setup and campaign configuration.

**Language:** Go  
**Source code:** [github.com/avnit/gophish](https://github.com/avnit/gophish)  
**Upstream:** [github.com/kgretzky/gophish](https://github.com/kgretzky/gophish)
