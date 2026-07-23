---
layout: post
title: "PVE-MooseFS"
subtitle: "A MooseFS storage plugin for Proxmox VE"
gh-repo: avnit/pve-moosefs
gh-badge: [star, fork]
tags: [projects, homelab, self-hosted, storage]
comments: false
---

pve-moosefs is a storage plugin that adds native support for [MooseFS](https://moosefs.com/) as a backend in Proxmox VE, so a distributed MooseFS cluster can host VM and container disks directly. This is my fork of [moosefs/pve-moosefs](https://github.com/moosefs/pve-moosefs), kept for my Proxmox cluster where I'm interested in distributed storage options.

## The concepts

The plugin registers MooseFS as a first-class Proxmox storage type. It supports clusters with passwords and subfolders, clean unmounting when storage is removed, and a high-performance MooseFS block-device (`mfsbdev`) mode. The headline capabilities for a virtualization cluster are live VM migration across hosts on MooseFS-backed storage and instant snapshots with near-instant rollbacks. The upstream project is explicit that it's still beta — snapshots in particular are flagged as experimental — so it's something I treat as evaluation rather than production-critical.

## How to use it

Once installed, you add MooseFS storage from **Datacenter → Storage → Add → MooseFS** in the web UI, or from the CLI:

```bash
pvesm add moosefs moosefs-vm-storage --path /mnt/mfs
```

Optional parameters let you point at a specific `--mfsmaster`, supply an `--mfspassword`, or mount an `--mfssubfolder`.

## Running it

It targets Proxmox VE 9.0 or newer. You can install a prebuilt `.deb` from the Releases page, or build from source with `make` and `dpkg -i *.deb`.

**Language:** Perl  
**Source code:** [github.com/avnit/pve-moosefs](https://github.com/avnit/pve-moosefs)  
**Upstream:** [github.com/moosefs/pve-moosefs](https://github.com/moosefs/pve-moosefs)
