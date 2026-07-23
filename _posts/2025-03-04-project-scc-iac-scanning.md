---
layout: post
title: "SCC IaC Scanning"
subtitle: "Sample infrastructure-as-code violations for Google Security Command Center"
gh-repo: avnit/scc-iac-scanning
gh-badge: [star, fork]
tags: [projects, security, google-cloud, terraform]
comments: false
---

SCC IaC Scanning is a collection of sample Infrastructure-as-Code files crafted to trigger the security violations that Google Security Command Center's IaC Validation service detects. This is my fork of the upstream samples, which sit squarely in my wheelhouse — validating Terraform against organization policies before it ever reaches production.

## The concepts

The idea behind shift-left IaC scanning is to catch misconfigurations at plan time rather than after deployment. SCC's IaC Validation service compares a Terraform plan against the organization policies and Security Health Analytics detectors defined for your Google Cloud org, and reports violations. This repo is deliberately full of bad configurations — concrete examples of common misconfigurations — so you can see exactly what each detector flags and confirm your scanning pipeline actually works. It doubles as a teaching resource for developers and security engineers learning what "good" versus "flagged" IaC looks like.

## How to use it

Checked-in code runs through a GitHub Actions pipeline that performs the IaC evaluation, authenticated via Workload Identity Federation. You can also run it locally against your own org if you have Security Command Center Premium or Enterprise enabled.

## Running it

```shell
terraform plan -out mainplan.tfplan
terraform show -json mainplan.tfplan > mainplan.json

gcloud scc iac-validation-reports create \
 organizations/$_ORGANIZATION_ID/locations/global \
 --tf-plan-file=mainplan.json \
 --format="json(response.iacValidationReport)" > IaCScanReport.json
```

These samples are for education and testing only, never for production.

**Language:** HCL
**Source code:** [github.com/avnit/scc-iac-scanning](https://github.com/avnit/scc-iac-scanning)
**Upstream:** [github.com/dreardon/scc-iac-scanning](https://github.com/dreardon/scc-iac-scanning)
