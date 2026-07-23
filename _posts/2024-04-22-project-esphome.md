---
layout: post
title: "ESPHome Room Sensors"
subtitle: "ESPHome configs from the Home Automator room-sensor build series"
gh-repo: avnit/esphome
gh-badge: [star, fork]
tags: [projects, esp32, iot, homelab, self-hosted]
comments: false
---

This is my fork of the ESPHome configuration files from the Home Automator YouTube channel's "let's build a room sensor" series. It collects the basic device setup and the step-by-step room-sensor configs that pair with the tutorials, and I keep it around because ESPHome runs the DIY sensors feeding my Home Assistant setup.

## The concepts

ESPHome lets you describe an ESP32 or ESP8266 device entirely in YAML — sensors, pins, WiFi, and the entities it exposes — and then compiles that into firmware you flash to the board. It integrates tightly with Home Assistant, so a room sensor built this way shows up automatically as temperature, humidity, or motion entities you can automate against. The repo is organized to follow the tutorial series: a basic setup common to all devices, then part 1 and part 2 of the room-sensor build.

## How to use it

You take the YAML for the device you want, adjust the pins and secrets for your hardware, and let ESPHome build and upload the firmware. From there the device reports into Home Assistant. Because it is a fork of the tutorial material, it is best read alongside the original videos rather than as a standalone product.

**Source code:** [github.com/avnit/esphome](https://github.com/avnit/esphome)
