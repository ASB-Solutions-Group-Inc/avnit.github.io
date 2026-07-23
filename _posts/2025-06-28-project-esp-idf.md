---
layout: post
title: "ESP-IDF"
subtitle: "Espressif's official IoT development framework"
gh-repo: avnit/esp-idf
gh-badge: [star, fork]
tags: [projects, esp32, iot, homelab]
comments: false
---

ESP-IDF is Espressif's official development framework for its SoCs, the toolchain and libraries you use to build firmware for ESP32-family chips on Windows, Linux, and macOS. This is my fork of [espressif/esp-idf](https://github.com/espressif/esp-idf), kept in my account for homelab firmware work and experimentation with ESP32 devices.

## The concepts

ESP-IDF gives you a component-based build system (`idf.py`), a menuconfig-driven configuration layer, FreeRTOS, and drivers for the chip's peripherals. Rather than a single static firmware, you compose an application from components, configure it, then build a bootloader, app, and partition table that flash onto the target. It's the foundation a lot of the IoT ecosystem sits on, including projects like ESPHome and WLED further up the stack.

## How to use it

The typical loop, once the environment is set up: pick or copy an example project, target your chip, configure, build, then flash over serial.

```bash
idf.py set-target esp32
idf.py menuconfig
idf.py build
idf.py -p PORT flash
```

Setup is a two-step install-and-export: run the install script (`install.sh` / `install.bat`) once, then source `export.sh` (or run `export.bat`) in each shell before use.

**Language:** C
**Source code:** [github.com/avnit/esp-idf](https://github.com/avnit/esp-idf)
**Upstream:** [github.com/espressif/esp-idf](https://github.com/espressif/esp-idf)
