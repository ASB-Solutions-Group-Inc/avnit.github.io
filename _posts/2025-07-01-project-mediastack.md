---
layout: post
title: "MediaStack"
subtitle: "A full Docker media stack with VPN-secured traffic and MFA remote access"
gh-repo: avnit/mediastack
gh-badge: [star, fork]
tags: [projects, docker, self-hosted, homelab]
comments: false
---

MediaStack is a complete Docker Compose setup for building a self-hosted media platform — Jellyfin or Plex alongside the full *ARR automation suite — with secure outbound traffic and multifactor remote access baked in. This is my fork of [geekau/mediastack](https://github.com/geekau/mediastack), and it maps directly to the media stack I actually run in my homelab.

## The concepts

The project's real value is that it wires dozens of containers together into one coherent, security-conscious stack. Media servers (Jellyfin, Plex) sit next to library managers (Radarr, Sonarr, Lidarr, Bazarr, Mylar) and an indexer manager (Prowlarr). Crucially, download traffic is routed through Gluetun so it only leaves the host over a VPN, CrowdSec provides collaborative intrusion prevention, and Authentik supplies SSO and MFA for remote access. Dashboards (Homarr, Homepage, Heimdall), monitoring (Prometheus, Grafana), and remote-access gateways (Guacamole, Headscale/Headplane) round it out.

## How to use it

You configure environment variables — paths, VPN credentials, domain, timezone — and bring up only the applications you want. The compose file is modular, so a minimal Jellyfin-plus-*ARR setup and a full monitored, SSO-gated deployment are the same project with different toggles.

## Running it

Deployment is Docker Compose driven from the project's `docker-compose.yaml` and env files. See the upstream [MediaStack.Guide](https://MediaStack.Guide) for the detailed, step-by-step configuration.

**Language:** Shell  
**Source code:** [github.com/avnit/mediastack](https://github.com/avnit/mediastack)  
**Upstream:** [github.com/geekau/mediastack](https://github.com/geekau/mediastack)
