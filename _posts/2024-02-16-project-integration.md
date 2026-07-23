---
layout: post
title: "HACS"
subtitle: "The Home Assistant Community Store, for custom integrations"
gh-repo: avnit/integration
gh-badge: [star, fork]
tags: [projects, home-assistant, self-hosted, iot]
comments: false
---

HACS — the Home Assistant Community Store — is an integration that gives you a UI for discovering, downloading, tracking, and updating custom elements for Home Assistant. This is my fork of [hacs/integration](https://github.com/hacs/integration), kept because Home Assistant runs in my homelab and HACS is how I manage the community add-ons on top of it.

## The concepts

Home Assistant's core ships a lot, but the ecosystem of community-built integrations and custom cards is enormous. HACS solves the discovery-and-lifecycle problem: instead of manually cloning repos into your config directory and remembering to pull updates, you browse available custom elements, install them in a click, and get update notifications and shortcuts to each project's repository and issue tracker — all from inside the Home Assistant UI.

## How to use it

Once HACS is set up, you use it from within Home Assistant to search for a custom integration or frontend card, install it, and keep it current. It effectively turns the sprawl of community add-ons into a managed store experience.

## Running it

HACS is installed as a custom integration into Home Assistant and then configured through the UI. See the upstream [HACS documentation](https://hacs.xyz/) for the current install and configuration steps.

**Language:** Python  
**Source code:** [github.com/avnit/integration](https://github.com/avnit/integration)  
**Upstream:** [github.com/hacs/integration](https://github.com/hacs/integration)
