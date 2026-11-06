---
layout: post
title: "CodeMender Triage MCP Server"
subtitle: "An MCP server on Cloud Run for triaging CodeMender findings in BigQuery, with logs and Wiz issues alongside"
gh-repo: avnit/codemender-mcp
gh-badge: [star, fork]
tags: [projects, python, security, google-cloud, ai-agents]
comments: false
---

A Model Context Protocol (MCP) server that runs on Google Cloud Run and lets an AI assistant inspect, query, and triage the security findings CodeMender publishes to BigQuery. It correlates each finding with execution, sandbox, and diagnostic traces from Cloud Logging, and it serves cloud security issues from Wiz through the same endpoint.

## The concepts

An automated remediation tool produces a lot of state: findings, generated patches, verification results, and failures. That data is only useful if someone can ask questions of it. This server turns it into tools a model can call, so triage becomes a conversation instead of a set of hand-written SQL queries.

**BigQuery — the findings**

- `list_codemender_issues` filters by severity, status, repository, CWE, date range, or text.
- `get_issue_details` returns code snippets, the generated patch, and verification results for one finding.
- `get_issues_summary` gives totals, open versus resolved, severity breakdown, and the top recurring vulnerabilities.
- `query_codemender_bigquery` runs read-only, parameterized SQL — `SELECT` and `WITH` only.

**Cloud Logging — the why**

- `get_issue_logs` pulls the compiler output, sandbox traces, and errors for a finding or session.
- `search_codemender_logs` searches across jobs for exceptions, sandbox policy violations, and scan failures.

**Wiz — the cloud context**

- Tools to list, summarize, and inspect Wiz issues, plus a read-only GraphQL query tool that rejects mutations. If Wiz isn't configured, those tools return an error and the rest of the server keeps working.

The server also ships MCP prompts — `triage_issue`, `triage_wiz_issue`, and `diagnose_remediation_failure` — that walk the model through an investigation: read the finding, fetch the correlated logs, review the patch, recommend the next action.

## Security design

Every data path is read-only. SQL is restricted to queries, GraphQL mutations are rejected, Google Cloud access uses Application Default Credentials rather than keys, and the container runs as a non-root user from a multi-stage build. Clients connect over HTTPS with an auth token.

## Running it

All settings, including the optional Wiz credentials, live in one `.env` file:

```bash
cp .env.example .env
# edit .env, then:
./deploy_cloud_run.sh
```

Locally, `config.py` reads the same `.env`. The repo includes unit tests with mocks for BigQuery, Cloud Logging, and Wiz, and a `cloudbuild.yaml` for CI/CD.

**Language:** Python  
**Source code:** [github.com/avnit/codemender-mcp](https://github.com/avnit/codemender-mcp)
