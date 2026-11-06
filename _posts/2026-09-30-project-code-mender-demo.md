---
layout: post
title: "CodeMender Orchestrator"
subtitle: "A three-stage pipeline that scans, verifies, patches, and opens pull requests inside your own infrastructure"
gh-repo: avnit/code-mender-demo
gh-badge: [star, fork]
tags: [projects, python, security, ci-cd, google-cloud, ai-agents]
comments: false
---

The CodeMender Orchestrator is an automated, multi-stage runner that executes inside an engineering team's own infrastructure — as GitHub Actions workflows or as Cloud Run Jobs and Workflows on Google Cloud. It automates vulnerability scanning, AI-driven verification, patch generation with the CodeMender CLI (`cm`), and pull request creation on GitHub.

## The concepts

To validate and fix a vulnerability, the tool has to run your codebase's own compilers, linters, and tests. A central backend cannot safely host thousands of custom build environments, so the orchestrator runs in your containers, in three stages.

**Stage 1 — Coordinator.** Clones the repository at a pinned commit and runs discovery with `cm find`. On a pull request it filters findings down to the lines the PR introduced or changed, so legacy issues don't block new work. It skips findings that already have an open fix PR, and prunes dead fix branches so leftovers never hide a real finding. With nothing actionable, it uploads a clean SARIF report and stops without starting any workers.

**Stage 2 — Parallel workers.** Findings are split into balanced shards and handed to short-lived workers: matrix jobs in GitHub Actions or parallel tasks in Cloud Run. Each worker verifies exploitability (`cm verify`), synthesizes and validates a patch (`cm fix`), pushes a branch, and opens a pull request. If PR creation fails, the branch is rolled back.

**Stage 3 — Aggregator.** Merges each worker's SQLite state shard, then produces HTML, JSON, and SARIF reports. It uploads the SARIF to GitHub Code Scanning, writes a step summary with severities, CWE IDs, links to the fix PRs, and LLM token usage by model, and enforces a blocking security gate on PR scans through a commit status check.

## Why it's built this way

- **Differential scanning** keeps the gate fair: a PR is judged on what it changed.
- **Deduplication** stops the same finding from producing a new PR every night.
- **A zero-finding fast path** means a clean repo costs almost nothing to scan.
- **Keyless authentication** — the Terraform under `terraform/` includes Workload Identity Federation for GitHub Actions.

## A compatibility note

The orchestrator was built and validated against a specific public-preview build of the CodeMender CLI. The CLI and its state database are still changing, so a newer `cm` binary may require changes to the parsers and the database merger. Pin the version you tested.

The repo has a broad unit test suite, a local end-to-end test, and architecture docs under `docs/`. Apache-2.0 licensed.

**Language:** Python  
**Source code:** [github.com/avnit/code-mender-demo](https://github.com/avnit/code-mender-demo)
