---
layout: post
title: "Evilginx2"
subtitle: "Reverse-proxy phishing framework for red-team engagements"
gh-repo: avnit/evilginx2
gh-badge: [star, fork]
tags: [projects, security, red-team]
comments: false
---

Evilginx is a man-in-the-middle framework that demonstrates how modern phishing can capture login credentials along with session cookies, which is what lets an attacker bypass two-factor authentication. This is my fork of Kuba Gretzky's [kgretzky/evilginx2](https://github.com/kgretzky/evilginx2), kept in my account for study as a security professional. As the upstream author states plainly, it should only be used in legitimate penetration testing with written permission from the parties being phished.

## The concepts

The interesting idea is the shift from cloning a login page to reverse-proxying the real one. Evilginx sits between the victim's browser and the genuine site, relaying traffic in both directions. Because the victim authenticates against the actual service, the framework can observe not just the password but the resulting session token, and a stolen session token sidesteps the second factor entirely. Written in Go, it ships its own HTTP and DNS servers, which is what makes the setup so self-contained.

For defenders, that's the whole lesson: MFA is necessary but not sufficient against real-time proxying. Phishing-resistant factors (hardware keys, WebAuthn), short session lifetimes, and origin binding are the countermeasures worth understanding here.

## Running it

Standing this up is intentionally out of scope for this post. If you have an authorized engagement, refer to the upstream project's official documentation at help.evilginx.com for installation and phishlet configuration.

**Language:** Go
**Source code:** [github.com/avnit/evilginx2](https://github.com/avnit/evilginx2)
**Upstream:** [github.com/kgretzky/evilginx2](https://github.com/kgretzky/evilginx2)
