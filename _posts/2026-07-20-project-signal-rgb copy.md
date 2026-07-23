---
layout: post
title: "Signal RGB"
subtitle: "Control SignalRGB lighting from Claude via MCP — with a wrapper that survives auto-updates"
gh-repo: avnit/signal-rgb
gh-badge: [star, fork]
tags: [projects, powershell, ai-agents, windows]
comments: false
---

Tooling that lets Claude Desktop, Claude Code, or any Model Context Protocol client drive SignalRGB on Windows in natural language — "set my RGB to a calm blue", "make the lights follow the screen" — plus a small CLI for scripting it directly.

## The concepts

SignalRGB (v2.5.72+) ships its own MCP server, `SignalRgbMcp.exe`, a stdio JSON-RPC server exposing roughly 60 tools: applying and installing effects, tweaking effect properties live, per-LED overrides, device settings and layouts, and app/debug logs. The catch is that SignalRGB installs into a version-specific folder under `%LOCALAPPDATA%\VortxEngine\app-<version>\`, so any MCP config pointing at that path silently breaks on the next auto-update. This repo is the glue: `signalrgb-mcp.cmd` resolves the newest installed version at launch time, so your config never goes stale.

## How to use it

Enable MCP in SignalRGB (Settings → Application → AI Integration, then restart the app — the toggle does nothing until restart), copy the wrapper somewhere stable, and register it:

```powershell
claude mcp add --scope user signalrgb -- cmd /c "%USERPROFILE%\.claude\mcp\signalrgb-mcp.cmd"
```

Claude Desktop users add the same command to `claude_desktop_config.json`. From there you can ask Claude to switch effects, sync the lights to whatever is on screen, or apply a beat-reactive audio visualizer.

There's also `srgb.ps1`, a CLI helper that performs the MCP handshake, makes one tool call, and exits — handy for scripting without any AI client:

```powershell
.\srgb.ps1 -Tool effect_apply -ArgsJson '{"name":"Screen Ambience"}'
```

Windows only, since SignalRGB itself is Windows-only. Audio-reactive effects listen to the system's default audio output, so Spotify or YouTube Music work with no per-app wiring.

**Language:** PowerShell
**Source code:** [github.com/avnit/signal-rgb](https://github.com/avnit/signal-rgb)
