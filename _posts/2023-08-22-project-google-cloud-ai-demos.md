---
layout: post
title: "Google Cloud AI Demos"
subtitle: "My fork of the official Vertex AI demo apps"
gh-repo: avnit/google-cloud-ai-demos
gh-badge: [star, fork]
tags: [projects, google-cloud, ai, web-dev]
comments: false
---

Frontend and backend code for Google Cloud's "AI Demos" — visual, interactive examples of what the platform's AI offerings can do. This is my fork of the official [GoogleCloudPlatform/google-cloud-ai-demos](https://github.com/GoogleCloudPlatform/google-cloud-ai-demos) repo, kept in my account for demo work and study; as a Customer Engineer specializing in AI on Google Cloud, having the demo source close at hand is genuinely useful.

## The concepts

These are explicitly not production apps — they exist to show, not just tell. The repo covers multiple demos across products and use cases, including:

- **Matching Engine** — a text and image search engine powered by Vertex AI Matching Engine (vector similarity search).
- **Time-series forecasting** — a forecasting app built with React, Material UI, Cloud Run, BigQuery, and Vertex AI.

The hosted versions live at [ai-demos.dev](https://ai-demos.dev/), so you can try them without deploying anything.

## How to use it

The most common way I use this repo is as reference code: when a customer asks "what does a real app on Matching Engine look like?", the answer is a working React frontend and a backend wired to actual Vertex AI APIs, not a slide. For deployment details, each demo's directory in the upstream repo documents its own setup.

**Language:** TypeScript

**Source code:** [github.com/avnit/google-cloud-ai-demos](https://github.com/avnit/google-cloud-ai-demos)
**Upstream:** [github.com/GoogleCloudPlatform/google-cloud-ai-demos](https://github.com/GoogleCloudPlatform/google-cloud-ai-demos)
