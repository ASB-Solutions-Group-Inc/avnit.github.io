---
layout: post
title: "Trustworthy ML Resource Hub"
subtitle: "A community resource site for trustworthy machine learning, built with MkDocs"
gh-repo: avnit/trustworthyml-ai.github.io
gh-badge: [star, fork]
tags: [projects, ai-agents, web-dev, learning]
comments: false
---

The Trustworthy ML Resource Hub is a documentation site that gathers course materials, research papers, tools, and community resources for trustworthy machine learning in one place. This is my fork of the upstream project, kept in my account because the topic — safety, robustness, and reliability in ML — sits close to my day-to-day work in AI and security.

## The concepts

The site is built with Material for MkDocs, which turns a tree of Markdown files into a searchable, themed static website. Content is organized into course materials (syllabus, schedule, assignments, projects), a curated research library, a tools-and-datasets section, and community pages. It is a good example of the "docs as a website" pattern: everything lives as plain Markdown under a `docs/` folder, and the framework handles navigation, full-text search, theming, and syntax highlighting.

## How to use it

Contributors edit Markdown files under `docs/` and preview locally before pushing. Deployment is automated with GitHub Actions, which builds the site and publishes it to GitHub Pages on every push.

## Running it

```bash
pip install -r requirements.txt
mkdocs serve
```

`mkdocs serve` runs a live-reloading preview at `localhost:8000`, and `mkdocs build` produces the static output in `site/` for production.

**Source code:** [github.com/avnit/trustworthyml-ai.github.io](https://github.com/avnit/trustworthyml-ai.github.io)
**Upstream:** [github.com/trustworthyml-ai/trustworthyml-ai](https://github.com/trustworthyml-ai/trustworthyml-ai)
