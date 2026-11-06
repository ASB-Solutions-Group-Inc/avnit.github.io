---
layout: post
title: "Hermes Watchlist"
subtitle: "A personal read-and-watch-next recommender across papers, Hacker News, blogs, podcasts, and video"
gh-repo: avnit/hermes-watchlist
gh-badge: [star, fork]
tags: [projects, javascript, python, ai-agents, web-dev]
comments: false
---

A personal tracker and recommender for Antigravity and Hermes material. It shows what to read or watch next, and when you mark something done it asks whether you liked it, then uses that answer to sharpen the next pick. It grew out of two static playlists ([Antigravity](https://github.com/avnit/antigravity-playlist) and [Hermes Agent](https://github.com/avnit/hermes-agent-playlist)): a fixed list of videos goes stale, and video is only one of the places good material shows up.

## The concepts

**Five sources, only one of them video.**

| Source | Where it comes from | Needs a key? |
| :--- | :--- | :--- |
| Papers | Hugging Face Papers search and the Daily Papers feed | No |
| Hacker News | The public Algolia API | No |
| Web | Blog and docs pages you list, scraped for on-topic links | No |
| Podcasts | RSS feeds you list | No |
| YouTube | YouTube Data API v3 | Yes |

Four of the five need no credentials, so a fresh clone produces a useful catalog with no setup.

**No backend, no database.** The app is static HTML, CSS, and JavaScript. A Python aggregator reads `data/sources.json` and writes `data/catalog.json`; the page reads the catalog. Your history lives in the browser's `localStorage` and never leaves your device.

**A recommender you can reason about.** Unread items are ranked by taste — topics, sources, and creators you've liked score higher, disliked ones lower, and newer items get a recency boost. The top pick appears as an "Up Next" hero with a short explanation of why it was chosen.

**A variety nudge.** Any feedback loop tends to collapse onto one platform. Here, sources you've consumed less than average get a score bump that scales with how lopsided your history is. Consume evenly and the term is close to zero; binge one source and the queue tilts toward the others. It tilts rather than vetoes, so a source you keep liking still wins.

## Running it

The app has to be served over HTTP, because browsers block `fetch` on `file://`:

```bash
./scripts/serve.sh    # http://localhost:8000/
```

It ships with real seed data. To pull live content, edit `data/sources.json` and run the fetcher, which uses only the Python standard library:

```bash
python3 scripts/fetch_media.py
```

Each source degrades gracefully: a missing API key or an unreachable feed is skipped with a warning and the rest still run. Both halves have tests — the aggregator with stubbed HTTP, the web app in a real Chromium page.

The live site is at [avnit.github.io/hermes-watchlist](https://avnit.github.io/hermes-watchlist/). MIT licensed.

**Language:** JavaScript, Python  
**Source code:** [github.com/avnit/hermes-watchlist](https://github.com/avnit/hermes-watchlist)
