---
layout: post
title: "Xonora iOS"
subtitle: "A native iPhone, Apple Watch, and CarPlay client for Music Assistant"
gh-repo: avnit/xonora-ios
gh-badge: [star, fork]
tags: [projects, ios, self-hosted, homelab]
comments: false
---

Xonora is a high-performance native client for [Music Assistant](https://music-assistant.io/), the open-source media player, running on iPhone, Apple Watch, and CarPlay. This is my fork of [hayupadhyaya/xonora-ios](https://github.com/hayupadhyaya/xonora-ios) — I keep it in my account because Music Assistant is part of my self-hosted stack and I like following the app's development closely.

## The concepts

The app is built in SwiftUI on top of a custom audio engine (SendspinKit) that aims for gapless, synchronized, high-fidelity playback streamed straight from a self-hosted server to your devices. The interesting architectural pieces are the ones that make streaming feel native across very different surfaces: a rebuilt CarPlay experience with tab-bar navigation (Home, Library, Queue, Now Playing), hardware-anchored lyrics that sync to the audio clock, and count-based pagination so large libraries load without hitting API limits.

## How to use it

You point Xonora at your Music Assistant server and browse or stream your library. Recent versions replaced the old access-token dance with proper username and password login, storing credentials securely in the iOS Keychain. From there you get library sort and view modes, grid customization, favorites you can heart from the CarPlay Now Playing screen, and synchronized queue control.

## Running it

Xonora is distributed through an open TestFlight beta rather than a build-it-yourself flow — you join the public TestFlight to install it and test new builds. See the upstream project for the current invite link and community Discord.

**Language:** Swift  
**Source code:** [github.com/avnit/xonora-ios](https://github.com/avnit/xonora-ios)  
**Upstream:** [github.com/hayupadhyaya/xonora-ios](https://github.com/hayupadhyaya/xonora-ios)
