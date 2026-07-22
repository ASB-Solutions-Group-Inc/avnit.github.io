---
layout: post
title: Homepage — Self-Hosted Homelab Dashboard
subtitle: "My customized fork of gethomepage/homepage, deployed with Docker on Proxmox"
gh-repo: avnit/homepage
gh-badge: [star, fork]
tags: [projects, homelab, docker, javascript, self-hosted]
comments: false
---

This is my personalized fork of [gethomepage/homepage](https://github.com/gethomepage/homepage) — the popular fully static, fast, highly customizable application dashboard — adapted to be the front door of my homelab at **homepage2.asbblog.com**.

## What it does

Homepage gives you a single pane of glass for every self-hosted service you run. Out of the box it supports **100+ service integrations** — the full *arr stack (Radarr, Sonarr, Bazarr), Jellyfin, Plex, Tautulli, download clients like qBittorrent and SABnzbd — plus information widgets for weather, time, search, and system stats via Glances. With Docker label discovery, new containers can show up on the dashboard automatically.

## What I changed

The upstream project is a Next.js app configured through YAML. My fork layers on the pieces that make it *mine*:

- **Personal config** — the `config/` directory carries my services, layout, and theming instead of the skeleton examples
- **One-command deploy** — a `run.sh` + `compose.yaml` pair that pulls my image from Docker Hub and brings the dashboard up on port 3000
- **Proxmox workflow** — deployment targets a Debian VM on my Proxmox cluster: clone, `docker login`, `./run.sh`, done
- **Docker integration baked into the deploy script**, so container discovery works from the first boot

## Security posture

Homepage widgets can surface personal information (home automation state, media libraries, system metrics) and the app deliberately ships **without an authentication layer**. Mine sits behind a reverse proxy on a trusted network — if you deploy something like this, put authentication, TLS, and host-header validation in front of it before exposing it anywhere untrusted.

**Stack:** Next.js / JavaScript, Docker Compose, deployed on Proxmox
**Source code:** [github.com/avnit/homepage](https://github.com/avnit/homepage) (fork of [gethomepage/homepage](https://gethomepage.dev/))
