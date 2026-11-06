---
layout: post
title: "Proxmox VE Helper-Scripts"
subtitle: "One-line installers for hundreds of self-hosted services on Proxmox"
gh-repo: avnit/ProxmoxVE
gh-badge: [star, fork]
tags: [projects, homelab, proxmox, self-hosted]
comments: false
---

The community edition of the Proxmox VE Helper-Scripts: a large collection of scripts that install and configure popular self-hosted services in a container or VM with a single command. This is my fork of [community-scripts/ProxmoxVE](https://github.com/community-scripts/ProxmoxVE), kept in my account as a reference for the Proxmox cluster in my homelab.

## The concepts

Every script follows the same pattern, which is what makes the collection trustworthy to use at scale:

- **Default mode** picks sensible CPU, RAM, and storage values and asks only the minimum questions. Most installs finish in under five minutes.
- **Advanced mode** gives you full control over container settings, networking, storage backend, and application configuration before anything is installed.

After installation, each container has a post-install helper, reachable from the Proxmox shell, for updating the service, changing settings, and basic troubleshooting.

The catalog covers home automation (Home Assistant, Zigbee2MQTT, ESPHome), media (Jellyfin, Plex, Immich), networking (AdGuard Home, Pi-hole, Traefik), monitoring (Grafana, Prometheus, Uptime Kuma), databases, security tools such as Vaultwarden and Authentik, and developer tools such as Gitea and n8n.

## How to use it

1. Go to [community-scripts.org](https://community-scripts.org) and search for the service you want.
2. Copy the one-line install command from the script page.
3. Paste it into the Proxmox shell and choose Default or Advanced.

It needs root shell access on a supported Proxmox VE host and an internet connection during installation.

A habit worth keeping: these scripts run as root on your hypervisor, so read a script before you pipe it into a shell. Having the fork makes that easy — the exact code is one click away.

**Language:** Shell  
**Source code:** [github.com/avnit/ProxmoxVE](https://github.com/avnit/ProxmoxVE)  
**Upstream:** [github.com/community-scripts/ProxmoxVE](https://github.com/community-scripts/ProxmoxVE)
