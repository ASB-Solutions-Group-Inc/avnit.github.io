---
layout: post
title: "Making Java Groovy"
subtitle: "Source code from Ken Kousen's Manning book"
gh-repo: avnit/Making-Java-Groovy
gh-badge: [star, fork]
tags: [projects, groovy, java, learning]
comments: false
---

My fork of [kousen/Making-Java-Groovy](https://github.com/kousen/Making-Java-Groovy), the companion source code for Ken Kousen's Manning book of the same name. Forked in 2012 while working through the book — one of the oldest repos in my account, and a snapshot of the era when Groovy was the pragmatic way to make Java development less ceremonious.

## What it is

The book's thesis was that you didn't have to abandon Java to enjoy Groovy — the two languages interoperate cleanly, so you could layer Groovy onto existing Java systems where its dynamic features, closures, and collection literals paid off most: builds, tests, scripting, and glue code. The repo mirrors that approach, organized by chapter, with each chapter containing one or more standalone projects.

## How to use it

Each project ships with its own Gradle build file, and most have their own README describing how to build and test. Clone it, pick a chapter, and run the Gradle build — the projects are intentionally small and self-contained, which made them easy to study alongside the text.

I keep the fork around as a bookmark from that phase of my JVM work; it's an unmodified copy of upstream. If the topic interests you, the upstream repo and the book itself are the places to go.

**Language:** Groovy  
**Source code:** [github.com/avnit/Making-Java-Groovy](https://github.com/avnit/Making-Java-Groovy) · Upstream: [kousen/Making-Java-Groovy](https://github.com/kousen/Making-Java-Groovy)
