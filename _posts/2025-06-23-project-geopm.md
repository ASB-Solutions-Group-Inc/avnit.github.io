---
layout: post
title: "GEOPM"
subtitle: "Fine-grained power monitoring and control for Linux systems"
gh-repo: avnit/geopm
gh-badge: [star, fork]
tags: [projects, linux, power-management, hpc]
comments: false
---

My fork of [geopm/geopm](https://github.com/geopm/geopm), the Global Extensible Open Power Manager — an open-source framework for low-latency batch access to power metrics and control knobs on Linux. I keep it in my account for study and experimentation; running a homelab full of Proxmox nodes where some machines stay powered down purely to save electricity makes power management software more than an academic interest.

## The concepts

GEOPM splits into two components. The Access Service is a privileged process exposing hardware signals and controls — CPU power draw, frequency limits, GPU power consumption — behind a platform-agnostic interface with per-user and per-group access control, even where the underlying hardware interfaces have none. The Runtime Service is an unprivileged process that adjusts platform settings based on feedback from those signals and from monitored application state. C, C++, and Python bindings exist for both layers.

Two design details stand out: user-driven hardware changes are automatically reverted when the user's session ends, and reads/writes can be gathered into batch operations to cut total latency. It also detects MPI and OpenMP phases in HPC applications and can generate per-phase energy reports.

## How to use it

The command-line tools give the flavor. Read total CPU power across the board:

```
geopmread CPU_POWER board 0
```

Cap the maximum CPU core frequency at 3.0 GHz (reverted when your session ends):

```
geopmwrite CPU_FREQUENCY_MAX_CONTROL board 0 3.0e9
```

## Installing it

Upstream ships installable packages for Fedora, Ubuntu, CentOS, Rocky, openSUSE, and RHEL, plus source builds and Spack integration — the [install guide](https://geopm.github.io/install.html) covers all of it.

**Language:** C++  
**Source code:** [github.com/avnit/geopm](https://github.com/avnit/geopm) · Upstream: [geopm/geopm](https://github.com/geopm/geopm)
