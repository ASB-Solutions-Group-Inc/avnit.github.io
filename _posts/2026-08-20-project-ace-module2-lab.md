---
layout: post
title: "CodeMender CI/CD Guardrail Lab"
subtitle: "A hands-on lab: an AI security agent that blocks risky deploys and opens the fix as a pull request"
gh-repo: avnit/ace-module2-lab
gh-badge: [star, fork]
tags: [projects, security, ci-cd, google-cloud, ai-agents, learning]
comments: false
---

A hands-on lab that wires Google CodeMender into a CI/CD pipeline as an autonomous security guardrail. When code is pushed, the pipeline scans it, blocks the deployment if it finds a HIGH or CRITICAL vulnerability, publishes a machine-readable report, and opens a pull request that patches the bug. The target application is OWASP Juice Shop, a deliberately vulnerable web app, so there is always something to find.

## The concepts

The lab teaches four ideas that apply well beyond this one tool:

- **An AI agent as a deployment gate.** The scan result becomes a red or green deploy decision in GitHub Actions, not a report someone reads later.
- **The real pipeline shape.** CodeMender runs as `find` (scan), then `report`, then `fix` (auto-patch).
- **Keyless CI authentication.** The workflow authenticates to Google Cloud with Workload Identity Federation instead of a long-lived service account key.
- **Autonomous remediation.** The agent does not stop at a finding; it opens a PR with a code fix for a human to review.

One point the lab makes early, and that I think every team should hear before adopting a tool like this: CodeMender is a cloud service with a local executor. The `cm` binary uploads your in-scope source to the service, where the analysis runs. Only point it at code you're allowed to share. Juice Shop is open source, so the lab is safe by construction, and the scan is scoped to the `routes/` folder, which holds the login SQL injection among other bugs.

## How to use it

The repo is the lab template. Students start at `lab/README.md`; instructors and graders have `lab/INSTRUCTOR.md`. The pieces that matter:

- `.github/workflows/codemender-pipeline.yml` — the guardrail workflow
- `.github/scripts/cm_triage.py` — turns the JSON report into a gate decision
- `CODEMENDER-LAB.md` — the overview

The rest of the repository is OWASP Juice Shop itself, which is MIT licensed.

**Language:** TypeScript  
**Source code:** [github.com/avnit/ace-module2-lab](https://github.com/avnit/ace-module2-lab)  
**Target app:** [github.com/juice-shop/juice-shop](https://github.com/juice-shop/juice-shop)
