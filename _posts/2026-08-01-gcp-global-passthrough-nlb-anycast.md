---
layout: post
title: "Anycast Without the Proxy: Google’s Global External Passthrough Network Load Balancer"
subtitle: "Global anycast routing for Layer 4 passthrough traffic — one IP worldwide, no proxy in the path"
tags: [google-cloud, networking, load-balancing, medium]
comments: false
canonical-url: https://medium.com/@avnitbambah/anycast-without-the-proxy-googles-global-external-passthrough-network-load-balancer-be81fb439d43
---

> Originally published on [Medium](https://medium.com/@avnitbambah/anycast-without-the-proxy-googles-global-external-passthrough-network-load-balancer-be81fb439d43).

Google Cloud just closed one of the longest-standing gaps in its load balancing portfolio. The global external passthrough Network Load Balancer, now in Preview, brings global anycast routing to Layer 4 passthrough traffic — something that until now forced you to choose between “global” and “passthrough.”

### The gap this fills

GCP’s load balancing lineup has always split along a clean line. Want global anycast with cross-region failover? Use a proxy-based load balancer — but accept connection termination at Google’s edge, TCP/HTTP-centric protocol support, and a proxy sitting between you and your clients. Want true passthrough — preserved source IPs, no termination, arbitrary IP protocols? You got it, but regionally scoped, with DNS-based geo-routing duct tape if you needed multi-region.

The new variant ends that trade-off. It’s a genuine passthrough load balancer — traffic arrives at your backends unterminated, client IPs intact — fronted by Google’s global anycast IP infrastructure. One IP address, advertised worldwide, steering each user to the closest region with healthy backends and available capacity, with dynamic cross-region failover when a region degrades.

### Why the protocol list is the real story

Look past the headline and read the supported protocols: TCP, UDP, ESP, GRE, ICMP, and ICMPv6, over both IPv4 and IPv6.

ESP and GRE are the tell. Those are tunnel protocols — IPsec and generic encapsulation. Combined with anycast and preserved addressing, this is purpose-built infrastructure for Security Service Edge platforms: a single global IP that terminates VPN and tunnel traffic in whichever region is closest to the user, with regional failure handled by routing rather than client reconfiguration. Google says as much, listing SSE first among target use cases, alongside DNS hosting, real-time bidding, RTC, live streaming, and gaming.

The common thread across those workloads: latency-sensitive, frequently UDP-based, and allergic to proxies. Adtech bidders and game servers have been building their own anycast on bare metal or renting it from CDN vendors for years. This puts that capability a forwarding rule away.

### The HA design worth stealing

The most architecturally interesting detail: each load balancer gets two external IP addresses, each served by a disjoint, isolated global control and data plane — Google calls these availability groups.

That’s a deliberate response to a failure mode every architect should respect: the global control plane itself as a single point of failure. Global anycast concentrates risk by design — one IP, one routing brain. Splitting the load balancer across two isolated infrastructure stacks means a bad rollout or control-plane fault in one group leaves the second IP serving. Your job is to actually use both — publish both IPs in DNS, or teach your clients to fail between them. An HA primitive you don’t wire up is decoration.

### Preview caveats

The usual Preview discipline applies. Backend regions are limited to twelve today — reasonable coverage across North America, Europe, Asia, South America, Africa, and Australia, but check your footprint before planning. More significantly, GKE backends aren’t supported in this release — instance groups and NEGs only for now. If your data plane lives in Kubernetes, this one isn’t ready for you yet.

### Bottom line

This is the most consequential GCP networking release in a while — not because anycast is new, but because anycast without a proxy in the path unlocks the protocols and workloads the proxy-based stack could never serve. If you operate VPN termination, DNS, or any latency-critical UDP service on GCP, this belongs in your lab this quarter.
