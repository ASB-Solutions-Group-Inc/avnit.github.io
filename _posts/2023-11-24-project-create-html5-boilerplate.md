---
layout: post
title: "Create HTML5 Boilerplate"
subtitle: "One-command scaffolding for an HTML5 Boilerplate site"
gh-repo: avnit/create-html5-boilerplate
gh-badge: [star, fork]
tags: [projects, web-dev, javascript]
comments: false
---

Create HTML5 Boilerplate is an `npx` quick-start that scaffolds a new site from the HTML5 Boilerplate template and gets you running with a single command. This is my fork of the upstream [create-html5-boilerplate](https://github.com/h5bp/create-html5-boilerplate) generator, kept in my account for reference.

## The concept

The idea mirrors tools like `create-react-app`: instead of cloning the full boilerplate repo and stripping out its build machinery, you run one command that fetches the latest published package, installs dependencies, bundles assets with Parcel, and opens a dev server. It's the low-friction on-ramp to a clean front-end starting point.

## How to use it

Any of the three package-manager entry points work:

```bash
npx create-html5-boilerplate new-site
cd new-site
npm install
npm start
```

That downloads the latest HTML5 Boilerplate, installs dependencies, and serves the site at `http://localhost:1234/`.

**Language:** JavaScript
**Source code:** [github.com/avnit/create-html5-boilerplate](https://github.com/avnit/create-html5-boilerplate)
**Upstream:** [github.com/h5bp/create-html5-boilerplate](https://github.com/h5bp/create-html5-boilerplate)
