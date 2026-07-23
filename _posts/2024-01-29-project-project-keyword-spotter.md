---
layout: post
title: "Project Keyword Spotter"
subtitle: "On-device keyphrase detection on a Coral Edge TPU — my fork of Google's demo"
gh-repo: avnit/project-keyword-spotter
gh-badge: [star, fork]
tags: [projects, ai, edge-computing, iot]
comments: false
---

A keyphrase detector (keyword spotter) that runs entirely on-device using a Google Coral Edge TPU. This is my fork of [google-coral/project-keyword-spotter](https://github.com/google-coral/project-keyword-spotter), the Google Research demo, kept in my account for Coral hardware experiments.

## The concepts

Keyword spotting is the speech-processing task behind hotwords like "OK Google" — detecting a predefined short phrase in a stream of audio. The model in this repo recognizes about 140 short keyphrases ("move left", "position four", and so on) in a two-second audio window, with each output neuron of the network corresponding to one phrase. Because inference runs on the Edge TPU, detection is fast, local, and needs no cloud round-trip — the same privacy-friendly, on-device pattern I like for homelab voice control.

## How to use it

Beyond the wrapper code, the repo ships three example programs:

- `run_model.py` — prints the top detections with confidence scores each time inference runs.
- `run_hearing_snake.py` — a voice-controlled version of the game Snake.
- `run_yt_voice_control.py` — controls a YouTube player in a browser tab with phrases like "next video" or "mute".

## Running it

You need a Coral Dev Board or USB Accelerator set up with the current runtime. Then:

```bash
sh install_requirements.sh
python3 run_model.py
```

Speak a supported keyphrase and you'll see it recognized in the console output with its confidence.

**Source code:** [github.com/avnit/project-keyword-spotter](https://github.com/avnit/project-keyword-spotter)
**Upstream:** [github.com/google-coral/project-keyword-spotter](https://github.com/google-coral/project-keyword-spotter)
