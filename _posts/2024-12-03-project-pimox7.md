---
layout: post
title: "Pimox 7"
subtitle: "Proxmox VE 7 ported to the Raspberry Pi"
gh-repo: avnit/pimox7
gh-badge: [star, fork]
tags: [projects, homelab, proxmox, raspberry-pi]
comments: false
---

My fork of [pimox/pimox7](https://github.com/pimox/pimox7), a port of Proxmox VE 7 to the Raspberry Pi. Pimox lets you build a Proxmox cluster out of Raspberry Pis — or a hybrid cluster mixing Pis with x86 hardware, which is exactly why it's in my account: my own Proxmox cluster includes a Pi whose whole job is holding a quorum vote.

## The concepts

Proxmox doesn't officially support ARM, so Pimox rebuilds the Proxmox VE packages for arm64 on top of Debian Bullseye. The repo itself contains the precompiled Debian packages; the original Proxmox sources live at git.proxmox.com, and the minimally patched sources used for the rebuild are in the pimox GitHub organization. The hybrid-cluster angle is the killer feature for homelabs — a $50 Pi makes a great low-power quorum node so a two-node x86 cluster can survive votes without a third full server burning watts.

## Running it

You need a Raspberry Pi 4 with a wired ethernet connection. The easy path is the interactive installer: flash the latest 64-bit Raspberry Pi OS, then as root:

```
curl https://raw.githubusercontent.com/pimox/pimox7/master/RPiOS64-IA-Install.sh > RPiOS64-IA-Install.sh
chmod +x RPiOS64-IA-Install.sh
./RPiOS64-IA-Install.sh
```

The manual route adds the Pimox apt repository and installs `proxmox-ve` — with the README's warning that you should use a locally attached console, since network connections get reset mid-install. A static IP, IPv6 removed from the interfaces file, and a proper hostname mapping are prerequisites.

**Source code:** [github.com/avnit/pimox7](https://github.com/avnit/pimox7) · Upstream: [pimox/pimox7](https://github.com/pimox/pimox7)
