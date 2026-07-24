---
layout: post
title: "JFrog SwampUp Demo — CI/CD for GKE"
subtitle: "Google Cloud Deploy + Cloud Build + JFrog Artifactory and Xray, end to end"
gh-repo: ASB-Solutions-Group-Inc/Jfrog-demo
gh-badge: [star, fork]
tags: [projects, google-cloud, ci-cd, kubernetes, devops]
comments: false
---

A demo I put together for **JFrog SwampUp 2022**: a complete CI/CD pipeline for Google Kubernetes Engine that combines Google Cloud tooling with JFrog's artifact management and security scanning. It's adapted from Google's [pop-kustomize](https://github.com/vszal/pop-kustomize) example.

## The concepts

The pipeline demonstrates how the two ecosystems fit together:

- **Cloud Build** builds the container on every check-in — the demo is driven by real git commits to simulate a developer workflow
- **JFrog Artifactory** serves as the artifact registry, with **JFrog Xray** scanning images for vulnerabilities before they ship
- **Google Cloud Deploy** promotes releases through three environments — test, staging, and prod — with **Kustomize overlays** handling the per-environment configuration differences

The sample workload is "Population Stats," a small Python Flask app that answers U.S. address queries with population data from the Census Bureau's Population Estimate API.

## How to use it

Fork the repo (the workflow depends on your own check-ins), then follow the setup tutorial in the README to wire up Cloud Build triggers, the Artifactory registry, and the Cloud Deploy delivery pipeline. From there, every push walks an image through build → scan → progressive promotion to GKE, and the architectural diagram in the repo maps each hop.

**Language:** Python
**Source code:** [github.com/ASB-Solutions-Group-Inc/Jfrog-demo](https://github.com/ASB-Solutions-Group-Inc/Jfrog-demo) (adapted from [vszal/pop-kustomize](https://github.com/vszal/pop-kustomize))
