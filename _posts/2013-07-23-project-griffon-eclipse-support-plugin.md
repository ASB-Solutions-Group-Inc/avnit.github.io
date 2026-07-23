---
layout: post
title: "Griffon Eclipse Support Plugin"
subtitle: "Keeping Eclipse classpaths in sync for Griffon apps — a fork from my Groovy days"
gh-repo: avnit/griffon-eclipse-support-plugin
gh-badge: [star, fork]
tags: [projects, groovy, java, dev-tools]
comments: false
---

A plugin for the Griffon framework (the Groovy-based desktop application framework) that keeps Eclipse project files up to date. This is my fork of [griffon-legacy/griffon-eclipse-support-plugin](https://github.com/griffon-legacy/griffon-eclipse-support-plugin), from my JVM/Groovy era in the early 2010s.

## The concepts

Griffon apps manage their own dependencies through plugins and an application `lib/` directory, which meant Eclipse's `.classpath` file constantly drifted out of sync with reality. This plugin fixes that with a single script, `eclipse-update`, that regenerates the `.classpath` file — and it runs automatically whenever a plugin is installed or uninstalled, so the IDE stays honest without manual bookkeeping. If you add or remove a library from `lib/` yourself, you run the script by hand.

## How to use it

Setup is mostly on the Eclipse side: define `USER_HOME` and `GRIFFON_HOME` classpath variables in the IDE so the generated entries resolve. Source directories under `griffon-app` and `src` are configured automatically, and extra ones can be declared in `BuildConfig.groovy`:

```groovy
eclipse.classpath.include = ['gen-src', '../app2/src']
```

This is a historical artifact now — Griffon has moved on and the upstream org is literally named "griffon-legacy" — but it's a nice reminder that developer-tooling glue code, the unglamorous kind, is often what keeps a team productive.

**Language:** Groovy

**Source code:** [github.com/avnit/griffon-eclipse-support-plugin](https://github.com/avnit/griffon-eclipse-support-plugin)
**Upstream:** [github.com/griffon-legacy/griffon-eclipse-support-plugin](https://github.com/griffon-legacy/griffon-eclipse-support-plugin)
