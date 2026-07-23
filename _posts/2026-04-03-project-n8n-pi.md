---
layout: post
title: "n8n-pi"
subtitle: "A preconfigured Raspberry Pi image that runs the n8n automation platform out of the box"
gh-repo: avnit/n8n-pi
gh-badge: [star, fork]
tags: [projects, self-hosted, homelab, raspberry-pi, automation]
comments: false
---

My fork of [TephlonDude/n8n-pi](https://github.com/TephlonDude/n8n-pi), a project that packages tools and images for building a Raspberry Pi preconfigured with [n8n](https://n8n.io) so it runs out of the box. I run n8n heavily in my homelab — it's the automation hub behind a lot of my workflows — so this fork lives in my account for reference and experimentation.

## The concepts

n8n is a no-code/low-code environment for connecting and automating different systems and services: workflows are built from connected nodes that receive, transform, and pass data between services, all through a web UI. The n8n-pi project exists to remove the two classic barriers to trying a new technology — hardware cost and installation friction — by shipping a working system on cheap, widely available hardware. For around $40 and a few minutes, you get a full n8n server.

## How to use it

Flash the preconfigured image to a Raspberry Pi and boot it; the upstream project's documentation site covers the details. The upstream README also points to an alternate path for people who prefer to install n8n themselves and run it under `systemd`.

This fork doesn't carry custom changes — it's here because self-hosted n8n on small hardware is squarely in my wheelhouse, and I like keeping a copy of the tooling close at hand.

**Language:** Shell
**Source code:** [github.com/avnit/n8n-pi](https://github.com/avnit/n8n-pi)
**Upstream:** [github.com/TephlonDude/n8n-pi](https://github.com/TephlonDude/n8n-pi)
