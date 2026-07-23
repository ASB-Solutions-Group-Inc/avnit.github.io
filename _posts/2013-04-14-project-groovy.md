---
layout: post
title: "Groovy"
subtitle: "A personal news dashboard that pulls my daily reads into one page"
gh-repo: avnit/Groovy
gh-badge: [star, fork]
tags: [projects, javascript, web-dev, learning]
comments: false
---

Groovy is an early personal project to build my own daily news dashboard — one page that pulls together the handful of things I actually read on the train each morning so I can glance at all of them in one place. Despite the name, it is a JavaScript project that calls the Google API to return results.

## The concepts

The idea was to return the top few results in each of the categories I care about — news, latest technology, sports, and business — and, importantly, to never show me the same story twice. That "read once, then hide it" logic is really a small state-management problem: track what has been seen and filter it out of future results. A planned second stage would add a word-a-day feature to the bottom of the page, pulling from a personal list of words I did not yet know, moving each shown word from a "to learn" file to a "learned" file, and topping the list back up from dictionary.com's API when it ran dry — even emailing me the new words.

## How I used it

This is very much an early experiment — a scratch project for scratching a personal itch and learning to stitch web APIs into a simple front end. The second stage stayed aspirational, but the core motivation (curate my own morning read instead of bouncing between sites) is one I still recognize.

**Language:** JavaScript
**Source code:** [github.com/avnit/Groovy](https://github.com/avnit/Groovy)
