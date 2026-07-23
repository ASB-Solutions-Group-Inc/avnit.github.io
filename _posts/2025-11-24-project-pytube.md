---
layout: post
title: "pytube"
subtitle: "My fork of the dependency-free Python YouTube downloader"
gh-repo: avnit/pytube
gh-badge: [star, fork]
tags: [projects, python, self-hosted]
comments: false
---

pytube is a lightweight, dependency-free Python library and command-line utility for downloading YouTube videos. This is my fork of the project, kept in my account for homelab use and experimentation — the upstream lives at [MarvinSchenkel/pytube](https://github.com/MarvinSchenkel/pytube), itself derived from the well-known [pytube](https://github.com/pytube/pytube) project.

## The concepts

What makes pytube appealing is its minimalism: it's pure Python with no third-party dependencies, and it handles both progressive and DASH streams, full playlists, caption tracks (with `.srt` export), and thumbnail capture. It also supports callback hooks like `on_progress` and `on_complete`, which makes it easy to pipeline downloads into larger scripts.

## How to use it

In a script, you instantiate a `YouTube` object with a video URL and filter the available streams:

```python
from pytube import YouTube
YouTube('https://youtu.be/2lAe1cqCOXo').streams.first().download()
```

There's also a CLI for one-off grabs:

```bash
pytube https://youtube.com/watch?v=2lAe1cqCOXo
```

## Installing it

```bash
python -m pip install pytube
```

Requires Python 3.6+. Full documentation is at [pytube.io](https://pytube.io).

**Source code:** [github.com/avnit/pytube](https://github.com/avnit/pytube)
**Upstream:** [github.com/MarvinSchenkel/pytube](https://github.com/MarvinSchenkel/pytube)
