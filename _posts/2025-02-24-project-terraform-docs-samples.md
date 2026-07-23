---
layout: post
title: "Terraform Docs Samples"
subtitle: "The Terraform samples behind cloud.google.com's how-to guides"
gh-repo: avnit/terraform-docs-samples
gh-badge: [star, fork]
tags: [projects, terraform, google-cloud]
comments: false
---

My fork of [terraform-google-modules/terraform-docs-samples](https://github.com/terraform-google-modules/terraform-docs-samples), the repository of Terraform samples intended for inclusion in Google Cloud's documentation. As a Customer Engineer at Google Cloud who lives in Terraform and GCP security architecture, this is a repo I reach for constantly — the samples here are what show up on the tabs of cloud.google.com how-to guides, like the one for creating a SQL Server instance on Compute Engine.

## The concepts

Every sample is written to the [Terraform sample guidelines](https://googlecloudplatform.github.io/samples-style-guide/) for quality and consistency, which makes the repo a useful style reference in its own right: if you want to see the canonical, documentation-grade way to express a GCP resource in HCL, it's probably in here.

## How to use it

The recommended path is Cloud Shell, since Terraform is preinstalled there and authentication is automatic — no service account keys to download:

```bash
git clone https://github.com/terraform-google-modules/terraform-docs-samples
```

From there, the standard Terraform workflow applies (`terraform init`, `plan`, `apply`), as described in Google Cloud's "Work with a Terraform configuration" basics guide. Contributions flow back through pull requests reviewed against the style guide.

My fork is unmodified — it's here so I always have a pinned copy of the samples I point customers at.

**Language:** HCL
**Source code:** [github.com/avnit/terraform-docs-samples](https://github.com/avnit/terraform-docs-samples)
**Upstream:** [github.com/terraform-google-modules/terraform-docs-samples](https://github.com/terraform-google-modules/terraform-docs-samples)
