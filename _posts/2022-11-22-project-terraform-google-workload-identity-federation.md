---
layout: post
title: "Terraform Workload Identity Federation"
subtitle: "Deploying Google Cloud Workload Identity Federation with Okta as the OIDC provider"
gh-repo: avnit/terraform-google-workload-identity-federation
gh-badge: [star, fork]
tags: [projects, terraform, google-cloud, security]
comments: false
---

This Terraform module deploys a Google Cloud Workload Identity Pool, Provider, and Service Account that an external identity can impersonate — with Okta as the OIDC provider in the reference architecture. Workload Identity Federation is one of my favorite security wins on GCP, so this fork of jasonbisson's module is a natural fit for my toolkit.

## The concepts

Workload Identity Federation lets external identities authenticate to Google Cloud without long-lived service-account keys. Instead of minting and distributing a key file, an external system presents a short-lived OIDC token, and Google exchanges it for temporary credentials based on attribute and claim mappings you define. This module sets up the full path: it creates the pool and provider, disables service-account key creation in the project (closing off the exact anti-pattern WIF exists to replace), creates the service account, and binds the IAM policy so the external identity can impersonate it via verified claims. A companion Python script generates the Okta OIDC token used to test the flow end to end.

## How to use it

You configure an Okta authorization server (issuer, audience, scope, and a custom claim for attribute verification), feed those values into `terraform.tfvars`, and apply. An included simple example deploys a Storage bucket using the federated credential so you can confirm the impersonation works and see the `serviceAccountDelegationInfo` in Cloud Logging.

## Running it

```
terraform init
terraform plan
terraform apply
```

Then generate the token and deploy the example bucket with `GOOGLE_APPLICATION_CREDENTIALS` pointed at the federated credential file.

**Language:** HCL
**Source code:** [github.com/avnit/terraform-google-workload-identity-federation](https://github.com/avnit/terraform-google-workload-identity-federation)
**Upstream:** [github.com/jasonbisson/terraform-google-workload-identity-federation](https://github.com/jasonbisson/terraform-google-workload-identity-federation)
