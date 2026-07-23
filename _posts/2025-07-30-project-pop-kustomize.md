---
layout: post
title: "Pop Kustomize"
subtitle: "End-to-end Google Cloud CI/CD for GKE, demoed with Kustomize overlays"
gh-repo: avnit/pop-kustomize
gh-badge: [star, fork]
tags: [projects, google-cloud, ci-cd, kubernetes]
comments: false
---

My fork of [vszal/pop-kustomize](https://github.com/vszal/pop-kustomize), a tutorial repo that demonstrates end-to-end CI/CD for GKE using Google Cloud's own tooling: Cloud Build, Artifact Registry, and Google Cloud Deploy. The demo app is "Population Stats," a small Python Flask service that pulls country population and flag data from the restcountries.com API.

## The concepts

The interesting part isn't the app — it's the pipeline. A git check-in triggers Cloud Build, which builds the container and pushes it to Artifact Registry; Google Cloud Deploy then promotes the release through three environments — test, staging, and prod. Kustomize overlays handle the configuration differences between those environments, so one base manifest serves all three with per-environment patches layered on top. It's a clean illustration of progressive delivery done with first-party GCP services instead of bolting on external CD tooling.

## How to use it

The upstream repo is explicitly designed to be forked — the demo relies on making your own git check-ins to simulate a developer workflow, which is exactly why this copy lives in my account. I use it when demonstrating Google Cloud CI/CD patterns to customers.

## Running it

The upstream README includes an interactive Cloud Shell tutorial that provisions everything step by step; you need a Google Cloud account and project, then the tutorial walks through enabling services, creating the GKE targets, and wiring up the delivery pipeline. If you'd rather read than click, the same walkthrough lives in `tutorial.md` in the repo.

**Source code:** [github.com/avnit/pop-kustomize](https://github.com/avnit/pop-kustomize) · Upstream: [vszal/pop-kustomize](https://github.com/vszal/pop-kustomize)
