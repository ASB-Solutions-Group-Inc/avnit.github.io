---
layout: post
title: "Swot"
subtitle: "JetBrains' registry of academic email domains, used to automate student-license approvals"
gh-repo: avnit/swot
gh-badge: [star, fork]
tags: [projects, kotlin, open-source]
comments: false
---

My fork of [JetBrains/swot](https://github.com/JetBrains/swot), the repository JetBrains uses to grant free tool licenses to students and teachers worldwide. It identifies email addresses and domains that belong to colleges and universities, which helps automate approving or rejecting academic discounts.

## The concepts

The heart of the repo is `lib/domains`: a hierarchically structured list of email domains owned by educational institutions, organized by country and TLD (so `unaab.edu.ng` lives at `lib/domains/ng/edu/unaab.txt`). Each domain is a single `.txt` file whose first line is the institution's official name, and adding a domain automatically covers all of its subdomains. There's also an `abused.txt` list of domains that were misused in the past and are no longer trusted — a nice reminder that any allowlist needs a revocation mechanism.

## How to use it

If your academic email domain is listed, you can request a free JetBrains license at their student page. To add an institution, you fork the repo, create the domain file in the right place in the hierarchy, and open a pull request; upstream reviews against clear criteria (the institution must offer at least one long-term IT-related course and be a recognized physical or accredited online school). Reviews typically take a few business days.

My fork is unmodified — I keep it around as a clean example of using a Git repository as a community-maintained dataset with a pull-request-driven approval workflow.

**Language:** Kotlin
**Source code:** [github.com/avnit/swot](https://github.com/avnit/swot)
**Upstream:** [github.com/JetBrains/swot](https://github.com/JetBrains/swot)
