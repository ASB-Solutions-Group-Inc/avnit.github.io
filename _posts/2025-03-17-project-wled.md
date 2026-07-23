---
layout: post
title: "WLED"
subtitle: "Feature-rich ESP32 firmware for addressable LEDs"
gh-repo: avnit/WLED
gh-badge: [star, fork]
tags: [projects, esp32, iot, homelab]
comments: false
---

My fork of [WLED](https://github.com/wled/WLED), the wildly popular open-source firmware for driving addressable LEDs — WS2812B, SK6812, APA102 and many more — from an ESP32 over WiFi. Originally created by Aircoookie and now community-maintained, it turns a two-dollar microcontroller and a strip of LEDs into a networked lighting system. This copy sits in my account for homelab use and tinkering; I haven't modified it.

## What makes it good

WLED ships over 200 built-in effects and 50+ palettes, with support for 2D matrices, HUB75 panels, and audio-reactive effects that respond to a microphone or line-in. Segments let you run different effects on independent parts of one strip simultaneously, and up to 250 presets (with playlists) cover the "save this exact look" use case.

The integration story is what earns it a place in a homelab: a JSON/HTTP API, MQTT with Home Assistant discovery, E1.31/Art-Net/DDP for professional lighting control, UDP sync across multiple WLED devices, Alexa voice control, and Philips Hue sync. With Home Assistant running on my cluster, WLED devices show up as first-class lights with essentially zero configuration.

## Running it

You flash the firmware to an ESP32 (all variants are supported — original, S2, S3, C3), connect your LED strip, and configure everything through the web UI it serves itself. Multi-WiFi with automatic AP fallback means it's never unreachable, and OTA updates handle everything after the first flash. The [documentation at kno.wled.ge](https://kno.wled.ge) has tutorials, a compatible-hardware list, and getting-started guides.

**Language:** C++  
**Source code:** [github.com/avnit/WLED](https://github.com/avnit/WLED) · Upstream: [wled/WLED](https://github.com/wled/WLED)
