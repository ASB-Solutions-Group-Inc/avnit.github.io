---
layout: post
title: "IPTV Player Sample"
subtitle: "Watch thousands of publicly available IPTV channels in the browser"
gh-repo: avnit/IPTV-Player-sample
gh-badge: [star, fork]
tags: [projects, self-hosted, media, web-dev]
comments: false
---

My fork of [Mravuri96/IPTV-Player](https://github.com/Mravuri96/IPTV-Player), a browser-based player for watching 8000+ publicly available IPTV channels. The upstream project wraps freely available channel playlists in a clean web interface, so streaming works directly in the browser with no client install.

## Why it's here

I run a fairly extensive self-hosted media stack in my homelab — Jellyfin, the *arr suite, and two dedicated media hosts — so open-source projects in the streaming space are a standing interest. This fork is kept in my account for study and experimentation with how browser-based IPTV playback is put together; I haven't made custom changes to it.

## The concepts

Projects like this typically build on the community-maintained public IPTV playlist collections: channels are published as M3U playlists, the player fetches and parses them, and playback happens with a JavaScript media player capable of handling HLS streams in-browser. The interesting engineering is in making thousands of channels searchable and startable quickly, not in the streaming itself — the browser's media stack does that heavy lifting.

The fork doesn't carry a README, so for documentation and a live demo, the upstream repo is the place to look.

**Source code:** [github.com/avnit/IPTV-Player-sample](https://github.com/avnit/IPTV-Player-sample) · Upstream: [Mravuri96/IPTV-Player](https://github.com/Mravuri96/IPTV-Player)
