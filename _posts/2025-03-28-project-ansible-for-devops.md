---
layout: post
title: "Ansible for DevOps"
subtitle: "Jeff Geerling's book examples — my go-to reference for automation patterns"
gh-repo: avnit/ansible-for-devops
gh-badge: [star, fork]
tags: [projects, ansible, devops, learning, homelab]
comments: false
---

My fork of [geerlingguy/ansible-for-devops](https://github.com/geerlingguy/ansible-for-devops), the example repository for Jeff Geerling's book *Ansible for DevOps*. Ansible is my preferred tool for keeping homelab changes idempotent and scriptable, and this repo is one of the best pattern libraries around, so I keep a copy in my account for reference.

## The concepts

The examples map to the book's chapters and cover an impressive range: a first playbook that installs and runs `chronyd`, multi-VM orchestration with ad-hoc commands, single-file LAMP/Drupal/Node.js/Solr playbooks that then get refactored into includes and roles, dynamic inventory scripts, and a highly available multi-server LAMP infrastructure. Later chapters get into the operational stuff I care about most — zero-downtime deployments behind HAProxy, rolling deployments, a security-hardening playbook, Jenkins CI/CD, Molecule testing in GitHub Actions, Let's Encrypt certificate automation, Docker image management, and even a playbook that builds a three-node Kubernetes cluster.

The upstream README is refreshingly honest that not every playbook follows every best practice — the examples are written to teach specific Ansible features clearly.

## Running the examples

Most examples use Vagrant and VirtualBox to boot local VMs that Ansible then configures, so you can experiment safely on a workstation:

```bash
git clone https://github.com/geerlingguy/ansible-for-devops
```

The book's manuscript is also freely available under CC BY-SA in a companion repository. This fork is unmodified — it's a reference shelf, not a divergence.

**Language:** Python
**Source code:** [github.com/avnit/ansible-for-devops](https://github.com/avnit/ansible-for-devops)
**Upstream:** [github.com/geerlingguy/ansible-for-devops](https://github.com/geerlingguy/ansible-for-devops)
