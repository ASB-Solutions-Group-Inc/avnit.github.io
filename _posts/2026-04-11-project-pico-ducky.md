---
layout: post
title: "Pico Ducky"
subtitle: "Turning a Raspberry Pi Pico into a USB Rubber Ducky for authorized testing"
gh-repo: avnit/pico-ducky
gh-badge: [star, fork]
tags: [projects, security, python, iot]
comments: false
---

Pico-ducky turns an inexpensive Raspberry Pi Pico into a USB Rubber Ducky style HID device — a keystroke-injection tool used in authorized penetration testing and security-awareness demonstrations. This is my fork of dbisu's project, kept in my account for study and lab use.

## The concepts

A keystroke-injection device presents itself to a host as a keyboard rather than storage, then "types" a scripted payload at machine speed. Because operating systems trust human-interface devices implicitly, this class of tool is a staple for demonstrating why physical port access matters and why endpoint policies should restrict unknown HID devices. The Pico runs CircuitPython and reads a Ducky Script payload from its filesystem. Responsible use is strictly for devices and environments you own or are explicitly authorized to test.

## How to use it

The project has a deliberate safety design. A jumper between GP0 and GND puts the device into setup mode so it will not inject its payload into your own machine while you are editing it. A second jumper option disables the USB mass-storage interface entirely for stealth during authorized engagements. You edit `payload.dd` on the CIRCUITPY drive to define what the device does.

## Running it

At a high level: flash the matching CircuitPython UF2 for your Pico, Pico W, or Pico 2 board, copy the `lib` folder and the `.py` files to the CIRCUITPY drive, enter setup mode, and drop in your payload. See the upstream README and releases for the full flashing steps.

**Language:** Python
**Source code:** [github.com/avnit/pico-ducky](https://github.com/avnit/pico-ducky)
**Upstream:** [github.com/dbisu/pico-ducky](https://github.com/dbisu/pico-ducky)
