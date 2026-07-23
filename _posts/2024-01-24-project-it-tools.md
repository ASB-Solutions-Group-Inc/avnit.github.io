---
layout: post
title: "IT Tools"
subtitle: "A self-hosted collection of handy online utilities for developers"
gh-repo: avnit/it-tools
gh-badge: [star, fork]
tags: [projects, self-hosted, web-dev, docker, homelab]
comments: false
---

IT Tools is a collection of handy web-based utilities for developers and IT people — token generators, encoders, converters, formatters, and dozens more — wrapped in a clean, fast UI. This is my fork of CorentinTh's project, which I self-host in my homelab so the tools stay a local tab away without depending on a public site.

## The concepts

The appeal here is consolidation and privacy. Instead of scattering across a dozen random websites to base64-encode a string, generate a UUID, parse a JWT, or format some JSON, you get them all in one Vue single-page app. Running it yourself means sensitive inputs never leave your network. Each tool is a self-contained component, and the project has a generator script that scaffolds a new tool's boilerplate, which makes it easy to extend.

## How to use it

You open the app and pick a tool from the categorized sidebar; everything runs client-side in the browser. For self-hosting, the simplest path is the Docker image — I run my own tagged build.

## Running it

```sh
docker run -d --name it-tools --restart unless-stopped -p 8080:80 abambah/it-tools:v3
```

There are also community packages for Cloudron, Tipi, and Unraid if you prefer an app-store install.

**Language:** Vue
**Source code:** [github.com/avnit/it-tools](https://github.com/avnit/it-tools)
**Upstream:** [github.com/CorentinTh/it-tools](https://github.com/CorentinTh/it-tools)
