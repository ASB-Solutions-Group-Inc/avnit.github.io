---
layout: post
title: "Workforce Identity Demo"
subtitle: "Copying Google Workspace group IAM bindings to a Workforce Identity Federation pool"
gh-repo: avnit/workflow-identity-demo
gh-badge: [star, fork]
tags: [projects, google-cloud, security, terraform, python]
comments: false
---

A demo for moving an organization from Google Workspace groups to Workforce Identity Federation without losing who has access to what. It pairs a Python script that copies existing IAM bindings with Terraform that provisions the workforce pool, the OIDC provider, and SCIM provisioning.

## The concepts

Workforce Identity Federation lets people sign in to Google Cloud with an external identity provider such as Entra ID or Okta, with no synced Google accounts. The hard part of adopting it is rarely the pool. It is the years of IAM bindings already granted to Workspace groups at the organization, folder, and project level.

The demo handles both halves:

1. **`copyIAM.py`** reads every Google Workspace group, scans the roles those groups hold across the organization, and grants the same roles to the equivalent Workforce Identity `principalSet` member.
2. **`terraform/`** provisions the Workforce Identity pool, an OIDC provider, and the SCIM integration — a service account, a Secret Manager secret, and the SCIM endpoint URL as an output.

The repo also carries a second Terraform module, `terraform-WIF/`, with Okta configuration, and a Cloud SQL variant of the copy script, `CopyIAM_CloudSQL.py`.

## How to use it

Set the four constants at the top of `copyIAM.py` (service account key file, delegated admin email, organization ID, pool ID) and run it. It starts in dry-run mode and changes nothing until you set `DRY_RUN = False`:

```bash
python3 copyIAM.py
```

Then deploy the pool and provider, always reviewing the plan first:

```bash
cd terraform
terraform init
terraform plan -out tf.out
terraform apply tf.out
```

After the apply, the Terraform outputs give you the SCIM endpoint URL and service account to paste into your identity provider's SCIM application.

Review the dry-run output carefully before applying. The script copies bindings as they are, so any over-broad grant a group holds today is carried over to the pool. A migration is a good moment to prune.

For the keyless CI/CD side of federation, see my earlier post on [GCP Workload Identity Federation with Okta](/2025-12-11-gcp-wif-okta/).

**Language:** Python, HCL  
**Source code:** [github.com/avnit/workflow-identity-demo](https://github.com/avnit/workflow-identity-demo)
