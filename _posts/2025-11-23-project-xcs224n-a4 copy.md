---
layout: post
title: "XCS224N Assignment 4"
subtitle: "Building a neural machine translation model for Stanford's NLP with Deep Learning course"
gh-repo: avnit/XCS224N-A4
gh-badge: [star, fork]
tags: [projects, python, ai-agents, learning]
comments: false
---

Coursework from Stanford's XCS224N (Natural Language Processing with Deep Learning), assignment 4 — training a neural machine translation model. This is where the theory of sequence-to-sequence learning turns into a model I actually had to build, train, and debug.

## The concepts

Assignment 4 in this course is the classic NMT exercise: an encoder-decoder architecture with attention. You implement the pieces that let a network read a source-language sentence, build up a context representation, and generate a translation token by token — including the attention mechanism that lets the decoder focus on relevant parts of the source at each step. Working through it makes the mechanics of embeddings, recurrent encoders, and beam-search decoding concrete rather than abstract.

## How I used it

The repository holds my implementation and the training setup for the assignment. The workflow is the usual deep-learning loop: fill in the model code, train on the provided parallel corpus, and evaluate translation quality, iterating on the parts that do not converge. It is a personal learning repo rather than a reusable library.

**Language:** Python
**Source code:** [github.com/avnit/XCS224N-A4](https://github.com/avnit/XCS224N-A4)
