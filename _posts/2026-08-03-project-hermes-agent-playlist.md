---
layout: post
title: "Hermes Agent Playlist"
subtitle: "A curated, agent-built page of the 20 best YouTube videos on Hermes Agent"
gh-repo: avnit/hermes-agent-playlist
gh-badge: [star, fork]
tags: [projects, ai-agents, learning, web-dev]
comments: false
---

A single-page site that collects the 20 best YouTube videos about Hermes Agent by Nous Research, sorted into a learning path. The fun part: the list was curated by Hermes Agent itself, so this repo doubles as a small test of what the agent can research, organize, and publish on its own.

## The concepts

When a new agent framework lands, the tutorials arrive faster than anyone can watch them. Instead of bookmarking videos at random, I had the agent pull the candidates, rank them, and group them into categories that match how you'd actually learn the tool:

- Quick Start & Fundamentals (3 videos)
- Full Tutorials & Courses (5 videos)
- Desktop & Advanced Use Cases (5 videos)
- Deep Dives & Experience (6 videos)
- Setup & Config (1 video)

Together the 20 videos account for more than 1.5M views as of August 2026.

## How it's built

There is no build step and no framework: the whole site is one `index.html`, deployed with GitHub Pages straight from the repo. That keeps the agent's job simple — regenerate one file, push, done.

The live page is at [avnit.github.io/hermes-agent-playlist](https://avnit.github.io/hermes-agent-playlist/). Its sibling for Google Antigravity is the [Antigravity Playlist](https://github.com/avnit/antigravity-playlist), and both later grew into the [Hermes Watchlist](https://github.com/avnit/hermes-watchlist) recommender.

**Language:** HTML  
**Source code:** [github.com/avnit/hermes-agent-playlist](https://github.com/avnit/hermes-agent-playlist)
