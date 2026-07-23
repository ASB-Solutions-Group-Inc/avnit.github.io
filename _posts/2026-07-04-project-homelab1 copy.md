---
layout: post
title: "Homelab Self-Hosted Stack"
subtitle: "Infrastructure-as-code and hardened runners for my Proxmox cluster"
gh-repo: avnit/homelab1
gh-badge: [star, fork]
tags: [projects, terraform, homelab, self-hosted, proxmox]
comments: false
---

Infrastructure-as-code and hardened runners for my Proxmox homelab — every component is either reproducible Terraform or a security-reviewed script, so nothing gets `curl | bash`-ed straight onto the hypervisor.

The repo started from a "self-hosting GitHub repos" video and got adapted to my two-node cluster (pve6 / pve7). Instead of copying commands blindly, I broke the ideas down into modules I can destroy and rebuild at will.

## The concepts

Three pieces live here:

- **`terraform/coolify/`** — a dedicated VM on pve7 running [Coolify](https://github.com/coollabsio/coolify), a self-hostable Heroku/Netlify/Vercel-style PaaS.
- **`terraform/khuedoan-homelab-sandbox/`** — an isolated throwaway VM for evaluating the alpha-stage [khuedoan/homelab](https://github.com/khuedoan/homelab) k3s/GitOps project, with zero contact with production workloads.
- **`proxmox-helper-scripts/`** — a hardened runner for the popular community Proxmox LXC installers. Rather than executing a live `main` branch as root on the hypervisor, it runs a pinned, audited SHA from my own fork.

The security posture is the point: secrets (`terraform.tfvars`, state files) are gitignored, alpha software runs in a sandbox, and anything that runs as root on the host runs from a commit I actually reviewed.

## Running it

Each Terraform module is self-contained. On the workstation side you need Terraform 1.5+ and an SSH keypair; on each Proxmox node, a snippets-enabled datastore and an API token.

```sh
cd terraform/coolify
cp terraform.tfvars.example terraform.tfvars
terraform init
terraform apply
terraform output
```

The helper-scripts hardening runs on the Proxmox host itself:

```sh
FORK_OWNER=avnit PIN_SHA=<reviewed_sha> ./proxmox-helper-scripts/harden-community-scripts.sh
```

**Language:** HCL

**Source code:** [github.com/avnit/homelab1](https://github.com/avnit/homelab1)
