---
layout: post
title: "VPC-SC Demo Terraform"
subtitle: "Terraform to stand up a GCP VPC Service Controls demo"
gh-repo: avnit/VPC-SC-Demo-Terraform
gh-badge: [star, fork]
tags: [projects, terraform, google-cloud, security]
comments: false
---

VPC-SC Demo Terraform provisions a Google Cloud VPC Service Controls demonstration environment from code, so you can see service perimeters protecting resources without clicking through the console. This is my fork of the demo repository, and VPC Service Controls is squarely in my wheelhouse as a GCP security specialist.

## The concepts

VPC Service Controls draws a security perimeter around GCP resources so that data can't be exfiltrated to projects or networks outside the boundary, even by an identity that otherwise has IAM permission. It's one of the strongest controls against data exfiltration in GCP, and it's also notoriously fiddly to configure by hand. Expressing a working perimeter in Terraform turns that into something reproducible: you can tear it down, rebuild it, and reason about the config in review.

## Running it

You need a GCP project to deploy into, plus org and billing details. After installing the tooling and authenticating, it's the standard Terraform loop:

```bash
gcloud auth login
gcloud auth application-default login
cd terraform
terraform init
terraform plan
terraform apply
```

The required variables are `org_id` and a `billing_account` on which you hold billing-user permissions.

**Language:** HCL
**Source code:** [github.com/avnit/VPC-SC-Demo-Terraform](https://github.com/avnit/VPC-SC-Demo-Terraform)
