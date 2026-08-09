---
layout: post
title: "GCP Cloud Run’s New Automated Failover Is a Direct Answer to a Real Outage"
subtitle: "Cross-region failover for Cloud Run goes GA six days after the europe-west4-a outage"
tags: [google-cloud, cloud-run, sre, medium]
comments: false
canonical-url: https://medium.com/@avnitbambah/gcp-cloud-runs-new-automated-failover-is-a-direct-answer-to-a-real-outage-81ccccc5c85e
---

> Originally published on [Medium](https://medium.com/@avnitbambah/gcp-cloud-runs-new-automated-failover-is-a-direct-answer-to-a-real-outage-81ccccc5c85e).

On July 15, 2026, a power and cooling failure took down Google Cloud’s europe-west4-a zone in the Netherlands for close to 15 hours. VMware Engine, Bare Metal Solution, and NetApp workloads pinned to that zone went dark with it. Six days later, Google pushed Cloud Run service health to General Availability — automated cross-region failover for Cloud Run services, built on infrastructure most of us already understand.

### What actually shipped

Service health uses the readiness probes you’re likely already running for instance-level health checks, and layers cross-region failover on top through serverless Network Endpoint Groups (NEGs). Setup is a two-click configuration in the console: point a global external Application Load Balancer at your service for public-facing traffic, or a cross-region internal ALB if the traffic is private. There’s no additional charge for the failover mechanism itself. “**Cloud Run automated cross-region failover Generally Available on July 21, 2026**”

### Why the timing matters

A real single-zone failure exposed exactly the gap this feature closes, and it landed in production before most teams had finished writing the postmortem action items from their own July outages.

That’s the pattern worth internalizing, independent of this specific release: cross-region failover is infrastructure you configure before you need it, not after. Readiness-probe-based routing isn’t new — what’s new is that Cloud Run now does the region-level orchestration for you instead of leaving it to hand-rolled scripts or a third-party traffic manager.

### Where this fits architecturally

For teams running latency-sensitive or compliance-bound workloads on Cloud Run in a single region “for now,” this removes the main excuse. Two failure modes it directly addresses:

- A zonal or regional outage (like the Netherlands incident) taking a public-facing service down with no automatic path to a healthy region.
- Internal services with cross-team dependencies where a regional blip cascades because nothing upstream knew to route around it.

The setup cost is genuinely low — this isn’t a multi-region active-active re-architecture, it’s turning on health-check-driven routing between regions you’re likely already deployed in for latency reasons.

### Takeaway

If a single-zone Cloud Run outage would actually hurt your business — customer-facing traffic, revenue-bearing APIs, anything with an SLA — this is worth an afternoon to configure this week, not a “someday” backlog item. The Netherlands outage was a reminder that “someday” arrives without notice.

### Limitations

The following limitations apply to Cloud Run service health:

- You must configure at least one service-level or revision-level [minimum instance](https://docs.cloud.google.com/run/docs/configuring/min-instances) per region to calculate health. You can also use the [Container instance count](https://docs.cloud.google.com/run/docs/monitoring#built-in_metrics) metric in Cloud Monitoring to estimate the required minimum instances for your regions.
- Failovers require at least two services from different regions. Otherwise, if one service fails, the error message `no healthy upstream` is displayed.
- You can’t configure a URL mask or tags in serverless NEGs.
- You can’t enable IAP from a backend service or load balancer. [Enable IAP directly from Cloud Run](https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run).
- If a Cloud Run service is deleted, Cloud Run doesn’t report an unhealthy status to the load balancer.
- Starting a new instance won’t count the first readiness probe, so a request might briefly route to a newly started service before becoming unhealthy.
- Cloud Run service health is computed across all instances. Revisions without probes are treated as unknown. The load balancer treats unknown instances as healthy.
- Service health computation might yield inaccurate results if instances are rapidly crashing.

### Sources

- [Automate cross-region failover with Cloud Run service health (Google Cloud Docs)](https://docs.cloud.google.com/run/docs/configuring/configure-service-health)
- [Cloud Run Automated Failover Goes GA Six Days After Google’s Netherlands Power Cut (TechTimes)](https://www.techtimes.com/articles/321186/20260721/cloud-run-automated-failover-goes-ga-six-days-after-googles-netherlands-power-cut.htm)
- [Google Cloud outage exposes datacentre resilience concerns (Computing.co.uk)](https://www.computing.co.uk/news/2026/datacentre/google-cloud-outage-exposes-datacentre-resilience-concerns)
- [Google Cloud experiences outage after power and cooling failure in Netherlands data center (DCD)](https://www.datacenterdynamics.com/en/news/google-cloud-experiences-outage-after-power-and-cooling-failure-in-netherlands-data-center/)

*I work on cloud security at Google Cloud and build things in a homelab on the weekends. More architecture write-ups at [avnit.asbblog.com](https://avnit.asbblog.com/).*
