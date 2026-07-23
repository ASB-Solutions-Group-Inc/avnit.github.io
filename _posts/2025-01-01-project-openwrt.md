---
layout: post
title: "OpenWrt"
subtitle: "A Linux OS for embedded networking devices"
gh-repo: avnit/openwrt
gh-badge: [star, fork]
tags: [projects, networking, homelab, self-hosted]
comments: false
---

OpenWrt is a Linux operating system for embedded devices, most famously home routers, that replaces vendor firmware with a fully writable filesystem and real package management. This is my fork of the OpenWrt source (itself a mirror of the canonical git.openwrt.org tree), kept in my account for homelab reference and experimentation.

## The concepts

Instead of a locked-down, static vendor image, OpenWrt gives you a proper Linux system you can extend with packages, which is what makes it the go-to for anyone who wants full control over their networking gear. For users that means customization the vendor never anticipated; for developers it's a framework to build a networked application on without assembling an entire firmware stack from scratch. In my own network it lives alongside the UniFi gear as a flexible, scriptable platform.

## How to use it

Most people never build it: the [Firmware Selector](https://firmware-selector.openwrt.org/) produces a factory image for supported devices that you flash over the vendor firmware. Building from source requires a Linux, BSD, or macOS host with a case-sensitive filesystem and the standard GNU toolchain, following the upstream Build System Setup docs.

**Language:** C
**Source code:** [github.com/avnit/openwrt](https://github.com/avnit/openwrt)
**Upstream:** [git.openwrt.org/openwrt/openwrt.git](https://git.openwrt.org/openwrt/openwrt.git)
