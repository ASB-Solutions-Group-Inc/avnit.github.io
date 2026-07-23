---
layout: post
title: "Jim's Garage"
subtitle: "A collection of homelab Docker Compose files and configs"
gh-repo: avnit/JimsGarage
gh-badge: [star, fork]
tags: [projects, homelab, docker, self-hosted]
comments: false
---

Jim's Garage is a well-known homelab resource: a collection of Docker Compose and config files that accompany [James Turland's](https://github.com/JamesTurland/JimsGarage) YouTube videos on self-hosting, Kubernetes, networking, and infrastructure. This is my fork, kept in my account as a reference library for my own Proxmox and Docker homelab.

## The concepts

The repo is deliberately practical — each folder maps to a video or topic and ships ready-to-adapt compose files and configuration rather than a framework. The idea is that you tweak the values to your own environment and deploy, using the videos to understand the "why" behind each setup.

## How to use it

Browse to the service or topic you're interested in, copy the relevant compose file, adjust volumes, networks, and environment variables for your hosts, and stand it up. Because it tracks real videos, it's a good way to learn a new tool end to end rather than just copying a config blind.

## Running it

Each directory is self-contained; the general pattern is `docker compose up -d` after editing the config to match your environment. Refer to the upstream repo and its accompanying videos for the specifics of any given stack.

**Language:** Shell  
**Source code:** [github.com/avnit/JimsGarage](https://github.com/avnit/JimsGarage)  
**Upstream:** [github.com/JamesTurland/JimsGarage](https://github.com/JamesTurland/JimsGarage)
