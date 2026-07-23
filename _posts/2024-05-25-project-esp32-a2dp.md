---
layout: post
title: "ESP32-A2DP"
subtitle: "Bluetooth audio on a microcontroller — my fork of the ESP32 A2DP library"
gh-repo: avnit/ESP32-A2DP
gh-badge: [star, fork]
tags: [projects, esp32, iot, audio]
comments: false
---

ESP32-A2DP is a simple Arduino library for Bluetooth A2DP audio on the ESP32 — build your own Bluetooth speaker (sink) or music sender (source) in a few dozen lines. This is my fork of [pschatzmann/ESP32-A2DP](https://github.com/pschatzmann/ESP32-A2DP), kept in my account for my own ESP32 audio tinkering.

## The concepts

The ESP32's Bluetooth stack can receive A2DP audio (say, from a phone) and hand you a PCM data stream decoded from SBC. Espressif's raw IDF example for this is clunky, so the upstream author wrapped it in a clean Arduino library. The typical flow is Bluetooth in, I2S out: I2S is the serial bus standard for moving PCM audio between chips, so you wire the ESP32's I2S pins to an external DAC and the library pipes the received stream straight through. AVRCP (remote control alongside A2DP) is supported too; hands-free and headset profiles are not.

## How to use it

The minimal Bluetooth-speaker sketch is genuinely tiny — using the recommended AudioTools library for I2S output:

```cpp
#include "AudioTools.h"
#include "BluetoothA2DPSink.h"

I2SStream i2s;
BluetoothA2DPSink a2dp_sink(i2s);

void setup() {
  a2dp_sink.start("MyMusic");
}

void loop() {}
```

That advertises a Bluetooth device called "MyMusic" and sends whatever you stream to it out over I2S. Pins are configurable, and output can also go through the native ESP32 I2S API, the internal DAC, or a data callback.

## Running it

Install the library (plus [AudioTools](https://github.com/pschatzmann/arduino-audio-tools)) in the Arduino IDE or PlatformIO, flash an example sketch, and pair your phone. Note the upstream is migrating off Espressif's legacy I2S API as of Arduino core v3 / IDF v5.

**Language:** C++

**Source code:** [github.com/avnit/ESP32-A2DP](https://github.com/avnit/ESP32-A2DP)
**Upstream:** [github.com/pschatzmann/ESP32-A2DP](https://github.com/pschatzmann/ESP32-A2DP)
