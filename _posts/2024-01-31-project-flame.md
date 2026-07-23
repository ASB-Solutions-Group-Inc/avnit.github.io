---
layout: post
title: "Flame"
subtitle: "A self-hosted startpage with built-in editors, search, and Docker auto-discovery"
gh-repo: avnit/flame
gh-badge: [star, fork]
tags: [projects, self-hosted, docker, homelab]
comments: false
---

My fork of [pawelmalak/flame](https://github.com/pawelmalak/flame), a self-hosted startpage for your server, design-inspired by SUI. With a homelab running dozens of services across multiple hosts, a good startpage is not a luxury — Flame is one of the nicer ones, and I keep this fork in my account for homelab use.

## The concepts

Flame's pitch is "no file editing necessary": applications and bookmarks are managed through built-in GUI editors, with pinning for favourites, an integrated search bar (local filtering plus 11 web search providers), an authentication layer to protect your settings, and heavy customization — custom CSS, 15 built-in color themes, and a theme builder. There's a weather widget, and — the killer feature for container-heavy setups — Docker integration that automatically discovers and adds apps based on container labels like `flame.name` and `flame.url`. The stack is Node.js + Express with Sequelize/SQLite on the back end and React + Redux + TypeScript on the front.

## Running it

Docker is the recommended route:

```sh
docker run -p 5005:5005 -v /path/to/data:/app/data -e PASSWORD=change_me pawelmalak/flame
```

A docker-compose variant mounts `/var/run/docker.sock` for the Docker integration, and every environment variable supports a `_FILE` suffix for Docker secrets, so the admin password never has to sit in the compose file. Multi-arch images cover Raspberry Pi-class ARM hardware.

This fork is unmodified — it's here so my homelab deployments track a copy I control.

**Language:** TypeScript
**Source code:** [github.com/avnit/flame](https://github.com/avnit/flame)
**Upstream:** [github.com/pawelmalak/flame](https://github.com/pawelmalak/flame)
