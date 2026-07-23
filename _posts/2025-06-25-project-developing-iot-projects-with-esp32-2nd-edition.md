---
layout: post
title: "Developing IoT Projects with ESP32, 2nd Edition"
subtitle: "Packt's ESP32 book code — sensors to cloud, with a detour into tinyML"
gh-repo: avnit/Developing-IoT-Projects-with-ESP32-2nd-edition
gh-badge: [star, fork]
tags: [projects, esp32, iot, learning]
comments: false
---

My fork of the official code repository for *Developing IoT Projects with ESP32, 2nd Edition* by Vedat Ozan Oner (Packt). ESP32 boards are the workhorses of my home automation experiments, so I keep this in my account as a study companion and reference.

## The concepts

The book takes an IoT system from the ground up on the ESP32 SoC: sensor communication over GPIO and I2C, useful libraries like LittleFS and LVGL, Wi-Fi in both station and AP modes with provisioning and the ESP RainMaker framework, and security measures including secure boot and OTA firmware updates. On the cloud side it covers AWS IoT for data handling and Grafana for real-time visualization. A dedicated section explores AI/ML for embedded systems — building and running tinyML applications on the ESP32-S3 with the Edge Impulse platform — and everything culminates in a full smart-home project.

Compared with the first edition, the examples are written in C++ against ESP-IDF (rather than C with PlatformIO), reflecting how Espressif's chip portfolio has grown: the budget RISC-V ESP32-C family on one end, and the AIoT-capable ESP32-S family on the other.

## How to use it

The code is organized per chapter, developed against Espressif devkits; upstream also maintains a branch with the examples updated for the newer ESP32-S3-BOX-3 devkit and ESP-IDF v5.2.2. This fork is unmodified — it exists so my own ESP32 tinkering has a pinned copy of the book's examples.

**Source code:** [github.com/avnit/Developing-IoT-Projects-with-ESP32-2nd-edition](https://github.com/avnit/Developing-IoT-Projects-with-ESP32-2nd-edition)
**Upstream:** [github.com/PacktPublishing/Developing-IoT-Projects-with-ESP32-2nd-edition](https://github.com/PacktPublishing/Developing-IoT-Projects-with-ESP32-2nd-edition)
