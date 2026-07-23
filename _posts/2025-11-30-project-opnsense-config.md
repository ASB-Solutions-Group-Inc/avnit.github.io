---
layout: post
title: "OPNsense Config"
subtitle: "Version-controlled configuration for my OPNsense router"
gh-repo: avnit/opnsense-config
gh-badge: [star, fork]
tags: [projects, homelab, networking, security]
comments: false
---

Configuration for an OPNsense router deployment — keeping firewall rules, interface layouts, and network services for my homelab under version control instead of living only inside the router's own backup files.

## Why keep router config in git

OPNsense stores its entire state in a single XML configuration, which makes it a natural fit for a git repo: every rule change becomes a diff you can review, and a bad change is one revert away. In a homelab with a Proxmox cluster, VLAN-separated services, and a media stack that all depend on the network behaving predictably, being able to answer "what changed and when" is worth a lot more than a nightly backup you never look at.

## What lives here

The repo tracks the configuration for my OPNsense deployment — the firewall rules, interfaces, and network services that shape traffic in the lab. It's a personal working repo rather than a template others should apply directly; firewall policy is very much a "your network, your rules" affair, and secrets never go into the config in plaintext.

If you want to do something similar, OPNsense makes it easy: the built-in configuration backup exports clean XML, and there are plugins that can push backups to a git remote automatically on every change.

**Source code:** [github.com/avnit/opnsense-config](https://github.com/avnit/opnsense-config)
