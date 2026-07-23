---
layout: post
title: "USB Uncensored LLM"
subtitle: "A zero-install, air-gapped local AI environment that runs from a USB drive"
gh-repo: avnit/USB-Uncensored-LLM
gh-badge: [star, fork]
tags: [projects, ai-agents, self-hosted, learning]
comments: false
---

USB-Uncensored-LLM is a fully air-gapped, zero-dependency local AI environment that runs directly from a hard drive or a portable USB/SSD. It ships with portable Python and isolated engine binaries so you can run large language models on any machine without an installer, package manager, or internet connection. This is my fork of the upstream project, kept in my account for homelab experimentation.

## The concepts

The design goal is portability without duplication. The project isolates operating-system executables from the heavy model weights: each platform (Windows, macOS, Linux, Android) gets its own launcher folder, while a single `Shared` volume holds the GGUF weights, chat history, and a portable Python environment. You download a multi-gigabyte model once and reuse it natively across every host you plug into. A custom-compiled Ollama engine underneath dynamically picks up AVX CPU instructions, NVIDIA CUDA, or Apple Metal depending on the machine.

## How to use it

You prepare the drive once, then launch the native menu for whichever OS you are on. A small Python HTTP server serves a dark-mode web UI, which means you can reach the model from a phone or tablet on the same WiFi without CORS gymnastics. It curates a library of ablated and fine-tuned models (Gemma, Qwen, NemoMix) for unfiltered local inference, and persists conversations across platforms.

## Running it

The upstream project ships offline installers and launchers per platform, so setup is largely a matter of copying the folder to a USB 3.0+ drive with at least 8 GB free (16 GB recommended) and running the native launcher. Note that upstream has since moved active development to a successor repository.

**Language:** HTML
**Source code:** [github.com/avnit/USB-Uncensored-LLM](https://github.com/avnit/USB-Uncensored-LLM)
