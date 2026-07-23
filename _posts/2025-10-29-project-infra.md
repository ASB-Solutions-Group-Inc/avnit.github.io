---
layout: post
title: "Infra"
subtitle: "Infrastructure-as-code for cloud and homelab"
gh-repo: avnit/infra
gh-badge: [star, fork]
tags: [projects, terraform, homelab, google-cloud]
comments: false
---

Infra is my Terraform/HCL repository for provisioning and managing infrastructure declaratively, so cloud and homelab resources are defined in version-controlled code rather than clicked together by hand.

## The concept

The point of infrastructure-as-code is repeatability: every network, project, service account, or VM is described in HCL, planned before it's applied, and reviewable in git. That makes changes auditable and rollbacks tractable, which matters as much for a homelab as it does for production cloud environments. Given my day-to-day in GCP security, this is also where idempotent, scriptable definitions of the boring-but-critical plumbing live.

## How to use it

The repo README is minimal for now, so the honest summary is: it's a working infra repo I develop against with the standard Terraform loop.

```bash
terraform init
terraform plan
terraform apply
```

**Language:** HCL
**Source code:** [github.com/avnit/infra](https://github.com/avnit/infra)
