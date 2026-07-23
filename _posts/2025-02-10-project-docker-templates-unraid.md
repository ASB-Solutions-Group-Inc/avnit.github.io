---
layout: post
title: "Docker Templates for Unraid"
subtitle: "Container templates for running services on Unraid"
gh-repo: avnit/Docker-Templates-Unraid
gh-badge: [star, fork]
tags: [projects, docker, self-hosted, homelab]
comments: false
---

Docker-Templates-Unraid is a set of Unraid Docker templates — the XML definitions that let Unraid's Community Applications plugin present containers as installable apps with a friendly configuration form. This is my fork, kept alongside the rest of my homelab tooling since Unraid runs a big chunk of my self-hosted stack.

## The concepts

Unraid wraps Docker with a template system. Each template is an XML file that describes a container: its image, port mappings, volume paths, environment variables, and the icons and descriptions that show up in the UI. Instead of remembering a long `docker run` line, you point Unraid at a template and it renders a form you can fill in and launch. Maintaining templates in a Git repo makes them portable and shareable across Unraid boxes.

## How I use it

On my Unraid server (a Dell R530 running Jellyfin, the *arr stack, and paperless-ngx among others), templates like these are what turn a raw image into a one-click install. Keeping them in version control means I can track changes and reapply a known-good configuration if I rebuild. As a fork it mirrors the upstream templates rather than adding custom ones.

**Source code:** [github.com/avnit/Docker-Templates-Unraid](https://github.com/avnit/Docker-Templates-Unraid)
