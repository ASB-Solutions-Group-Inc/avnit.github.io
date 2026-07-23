---
layout: post
title: "Home Assistant Frontend"
subtitle: "The web UI for the Home Assistant platform"
gh-repo: avnit/frontend
gh-badge: [star, fork]
tags: [projects, home-assistant, web-dev, homelab]
comments: false
---

This is the official web frontend for [Home Assistant](https://home-assistant.io), the open-source home-automation platform, the dashboard and UI you interact with in the browser. This is my fork of [home-assistant/frontend](https://github.com/home-assistant/frontend), kept in my account for study and homelab tinkering, since Home Assistant (HAOS) runs on my Proxmox cluster.

## The concepts

The frontend is a TypeScript single-page application that talks to the Home Assistant core over its WebSocket API, rendering entities, dashboards (Lovelace), and configuration flows. It's Apache-2 licensed and designed to be browsed and learned from, which is exactly why I keep a copy: it's a good reference for how a large, real-world TypeScript UI is structured, and a place to experiment against my own instance.

## How to use it

For development the upstream flow is `script/setup` for initial setup, then the development instructions in the Home Assistant developer docs, with `script/build_frontend` for a production build. Day to day, though, most people simply run the frontend as it ships inside Home Assistant rather than building it themselves.

**Language:** TypeScript
**Source code:** [github.com/avnit/frontend](https://github.com/avnit/frontend)
**Upstream:** [github.com/home-assistant/frontend](https://github.com/home-assistant/frontend)
