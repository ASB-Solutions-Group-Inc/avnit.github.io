---
layout: post
title: "Arrstack"
subtitle: "Terraform for Proxmox VMs, plus assorted automation scripts"
gh-repo: avnit/arrstack
gh-badge: [star, fork]
tags: [projects, terraform, homelab, proxmox]
comments: false
---

A working repo of homelab automation, centered on Terraform configuration that deploys virtual machines on my Proxmox server. Despite the name, it grew into a small grab-bag of infrastructure and scripting work.

## What's inside

The main piece is the `terraform/` folder: `main.tf` defines the resources to create — a Debian VM and a Home Assistant VM — and uses remote-exec provisioners to run setup scripts on both the Proxmox host and the freshly created guests. `variables.tf` holds the Proxmox connection details and other tunables, so pointing it at a different node is a variable change, not a rewrite. There's also a shell script for configuring BGP routing on a router with route-maps.

Alongside that sits a `Consulting-upwork/` folder with a Python script that fetches job information from the Upwork API (via the `python-upwork` library) — unrelated to the media stack, but this repo was the workbench at the time.

## Running it

You need Terraform installed and API access to a Proxmox server. Fill in your connection details in `variables.tf`, then the usual cycle applies:

```sh
terraform init
terraform apply
```

The Upwork script needs `pip install python-upwork` and your own API key and secret.

This repo is an earlier iteration of the approach I later cleaned up in [homelab1](https://github.com/avnit/homelab1), where the Terraform is modular and secrets handling is stricter.

**Language:** HCL

**Source code:** [github.com/avnit/arrstack](https://github.com/avnit/arrstack)
