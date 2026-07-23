---
layout: post
title: "Terraform Google Influx"
subtitle: "Terraform modules for running the TICK stack on Google Cloud"
gh-repo: avnit/terraform-google-influx
gh-badge: [star, fork]
tags: [projects, terraform, google-cloud, monitoring]
comments: false
---

My fork of [influxdata/terraform-google-influx](https://github.com/influxdata/terraform-google-influx), a set of reusable Terraform modules for running the TICK stack — Telegraf, InfluxDB, Chronograf, and Kapacitor — on Google Cloud.

## The concepts

The TICK stack is InfluxData's time-series platform: Telegraf collects metrics, InfluxDB stores them, Chronograf visualizes, and Kapacitor alerts. These modules codify a GCP deployment of that stack in HCL, so the whole thing is reproducible with a plan/apply cycle rather than hand-built VMs.

The module layout in my fork's README shows the working parts: a `tick-instance-group` module that stands up InfluxDB nodes as a managed instance group, a dedicated service-account module, and a substantial set of firewall resources — including rules for IAP-tunneled SSH and RDP, private Google APIs egress, and deliberate deny-all-egress defaults — plus Cloud DNS zones for private Google API access. That firewall-and-DNS posture reflects the kind of locked-down GCP network baseline I work with professionally: no public ingress, admin access only through Identity-Aware Proxy, and private connectivity to Google APIs.

## How to use it

The modules take the usual inputs — project ID, region, machine type, and a source image for the InfluxDB nodes — and output the instance group self-links. As with any Terraform module collection, you compose them from your own root module and run `terraform apply` against a GCP project. For general TICK-on-GCP usage, upstream's documentation and examples are the reference point.

**Language:** HCL  
**Source code:** [github.com/avnit/terraform-google-influx](https://github.com/avnit/terraform-google-influx) · Upstream: [influxdata/terraform-google-influx](https://github.com/influxdata/terraform-google-influx)
