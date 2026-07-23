---
layout: post
title: "webretro"
subtitle: "RetroArch in the browser — my fork of the WebAssembly port"
gh-repo: avnit/webretro
gh-badge: [star, fork]
tags: [projects, self-hosted, gaming, web-dev]
comments: false
---

webretro is [RetroArch](https://github.com/libretro) ported to WebAssembly with emscripten — a full retro-gaming frontend that runs entirely in the browser. This is my fork of [BinBashBanana/webretro](https://github.com/BinBashBanana/webretro), kept in my account so I can self-host an instance on my own infrastructure.

## The concepts

The repo ships with more than twenty pre-built libretro cores covering everything from the NES, SNES, and Genesis to the PlayStation, Nintendo DS, and Nintendo 64 (ROMs are not included). Everything is client-side: save states and SRAM persist to the browser's indexedDB per ROM, with SRAM autosaving every five minutes, and users can import/export saves, take screenshots, apply cheat codes, and use a curated set of CRT and upscaling shaders. It even installs as a PWA.

## How to use it

Serve the static files and open the page — the user uploads a ROM directly or from Google Drive/Dropbox/OneDrive. Behavior is controlled by query-string options: `core` picks a specific libretro core, `system` autodetects by platform, and `rom` can fetch a ROM from the server's `roms/` directory or an absolute URL. For example:

```
?core=snes9x&rom=game.smc
?core=autodetect&nobundle
```

There's also an embedding API (`embed/embed.js`) for dropping a webretro iframe into another site.

## Running it

As a fork of a static web app, deployment is just hosting the repo — GitHub Pages upstream, or any web server on the homelab. By default the asset bundle is fetched from GitHub via jsdelivr, which can be repointed to a local path in `assets/base.js` for a fully self-hosted setup. Building the cores from source is documented in the `source/` directory.

**Source code:** [github.com/avnit/webretro](https://github.com/avnit/webretro)
**Upstream:** [github.com/BinBashBanana/webretro](https://github.com/BinBashBanana/webretro)
