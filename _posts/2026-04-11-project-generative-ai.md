---
layout: post
title: "Generative AI on Google Cloud"
subtitle: "Google's sample notebooks and apps for Gemini on Vertex AI"
gh-repo: avnit/generative-ai
gh-badge: [star, fork]
tags: [projects, google-cloud, ai-agents, learning]
comments: false
---

This is my fork of [GoogleCloudPlatform/generative-ai](https://github.com/GoogleCloudPlatform/generative-ai), Google's official collection of notebooks, code samples, and sample apps for building generative AI workflows on Google Cloud with Gemini and Vertex AI. As a Customer Engineer focused on AI and security at Google Cloud, I keep it forked for reference and hands-on experimentation.

## The concepts

The repo is organized by capability rather than by tutorial, which makes it a good map of the platform. The `gemini/` folder covers starter notebooks, function calling, and sample apps; `search/` demonstrates Agent Search for building search over websites and enterprise data; `rag-grounding/` indexes everything related to Retrieval Augmented Generation and grounding; and `vision/` and `audio/` show building from scratch with Imagen, Veo, and Chirp. There's also a `setup-env/` guide for getting the Gen AI Python SDK running in Colab or Vertex AI Workbench.

## How to use it

Most of the material lives in Jupyter notebooks you can open in Colab or Workbench, authenticate against a Google Cloud project, and run cell by cell. It's the fastest way to go from "what can Gemini do on Vertex AI" to working code you can adapt into your own solutions.

## Running it

Follow the `setup-env/` instructions to configure Google Cloud, install the Gen AI Python SDK, and open the notebooks in a Colab or Workbench environment.

**Language:** Jupyter Notebook  
**Source code:** [github.com/avnit/generative-ai](https://github.com/avnit/generative-ai)  
**Upstream:** [github.com/GoogleCloudPlatform/generative-ai](https://github.com/GoogleCloudPlatform/generative-ai)
