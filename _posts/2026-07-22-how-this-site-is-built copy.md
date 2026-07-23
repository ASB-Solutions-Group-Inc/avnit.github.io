---
layout: post
title: How This Site Is Built
subtitle: The architecture behind avnit.asbblog.com — Jekyll, GitHub Pages, and an AI-assisted workflow
gh-repo: ASB-Solutions-Group-Inc/avnit.github.io
gh-badge: [star, fork]
tags: [architecture, jekyll, github-pages, projects]
comments: false
---

This site is intentionally boring in the best way: **no servers, no database, no build pipeline to babysit**. Here's a tour of how it works, from a markdown file on my machine to the page you're reading.

## The big picture

```text
┌─────────────────┐     git push      ┌──────────────────────────┐
│  Local editing   │ ────────────────▶ │  GitHub repo (master)    │
│  Markdown posts  │   (via PRs)       │  ASB-Solutions-Group-Inc │
│  + Claude Code   │                   │  /avnit.github.io        │
└─────────────────┘                   └────────────┬─────────────┘
                                                    │ automatic build
                                                    ▼
                                       ┌──────────────────────────┐
                                       │  GitHub Pages (Jekyll)   │
                                       │  markdown ──▶ static HTML │
                                       └────────────┬─────────────┘
                                                    │ CDN
                                                    ▼
                              DNS CNAME record      ┌──────────────┐
                     avnit.asbblog.com ───────────▶ │  You, reading │
                                                    └──────────────┘
```

## The stack, layer by layer

### 1. Jekyll — the static site generator

Every post on this site is a plain **markdown file** in the `_posts/` directory, named like `2026-07-22-how-this-site-is-built.md`. Each file starts with a small YAML "front matter" block declaring its title, subtitle, and tags. When the site builds, [Jekyll](https://jekyllrb.com/) turns each markdown file into a static HTML page — there is no server-side code and nothing to hack or patch at runtime.

That's a deliberate security choice as much as a convenience: a static site has a tiny attack surface. No admin panel, no plugin updates, no SQL.

### 2. Beautiful Jekyll — the theme

The layout, navbar, tag system, search, and RSS feed come from [Beautiful Jekyll](https://beautifuljekyll.com/), a popular open-source Jekyll theme. Almost everything about it is driven by a single `_config.yml` file — site title, navigation links, social icons, colors, and pagination.

On top of the theme sits one custom stylesheet, `assets/css/custom-styles.css`, which restyles the whole site into the dark look you're seeing: the gradient headings, the glassy fixed navbar, and the card grid on the home page. The theme loads it through the `site-css` config option, so the theme itself stays unmodified and easy to update.

### 3. GitHub Pages — hosting and CI in one

The entire site lives in a public GitHub repository. **GitHub Pages watches the `master` branch**: every merge triggers an automatic Jekyll build, and the output is served from GitHub's global CDN. That means the deployment pipeline is just `git push` — no GitHub Actions workflow, no build server, no FTP.

### 4. Custom domain — one DNS record

A `CNAME` file in the repo tells GitHub Pages the site answers at `avnit.asbblog.com`, and a matching CNAME record in DNS points that subdomain at GitHub's servers. GitHub provisions the TLS certificate automatically.

### 5. The content — generated from GitHub itself

The project posts on the home page weren't written one by one. They were **generated from the GitHub API**: a script pulled every original (non-fork) repository from [github.com/avnit](https://github.com/avnit), and turned each one into a markdown post dated by the repo's creation date. New project, new repo, one more markdown file.

### 6. The workflow — AI-assisted, PR-gated

The site is maintained with [Claude Code](https://claude.com/claude-code). Changes happen on a branch in an isolated git worktree, land as a pull request, and only reach the live site when the PR merges to `master`. That keeps a clean, reviewable history — every change to this site, including this post and the redesign that shipped with it, is a commit you can read.

## Why this architecture

| Concern | How it's handled |
| :--- | :--- |
| Hosting cost | $0 — GitHub Pages is free for public repos |
| Security | Static HTML only; no runtime, no database |
| Deploys | Automatic on merge to `master` |
| Backups | The site *is* a git repo — full history, trivially cloneable |
| Writing | One markdown file per post, no CMS |
| Design | One theme + one custom CSS file |

If you want to build the same thing, fork [Beautiful Jekyll](https://github.com/daattali/beautiful-jekyll), edit `_config.yml`, and turn on GitHub Pages in your repo settings. Total time to a live site: about ten minutes.
