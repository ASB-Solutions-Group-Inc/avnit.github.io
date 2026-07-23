---
layout: post
title: "GeminiCoder"
subtitle: "Generate small apps from a single prompt with the Gemini API"
gh-repo: avnit/geminiCoder
gh-badge: [star, fork]
tags: [projects, ai-agents, web-dev, google-cloud]
comments: false
---

GeminiCoder (upstream: InstantCoder) is a small web app that generates working single-prompt apps using the Gemini API. This is my fork of [osanseviero/InstantCoder](https://github.com/osanseviero/InstantCoder), which is itself based on Nutlope's llamacoder. Given my focus on generative AI at Google Cloud, I keep it as a compact, readable example of wiring Gemini into an interactive code-generation UI.

## The concepts

The app takes a natural-language prompt, calls Gemini to produce app code, and renders it live in a sandbox. The stack is deliberately minimal and modern: the Gemini API (with support for Gemini 1.5 Pro, 1.5 Flash, and 2.0 Flash Experimental), Sandpack for the in-browser code sandbox, and Next.js with the app router and Tailwind for the frontend. It's a clean demonstration of the "prompt in, running app out" loop that model-powered coding tools are built around.

## How to use it

You enter a prompt describing the small app you want, and the generated code appears and runs in the Sandpack sandbox so you can iterate immediately.

## Running it

```bash
git clone https://github.com/osanseviero/GemCoder
```

Create a `.env` file with your Google AI Studio API key (`GOOGLE_AI_API_KEY=`), then run `npm install` and `npm run dev` to start it locally.

**Language:** TypeScript  
**Source code:** [github.com/avnit/geminiCoder](https://github.com/avnit/geminiCoder)  
**Upstream:** [github.com/osanseviero/InstantCoder](https://github.com/osanseviero/InstantCoder)
