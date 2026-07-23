---
layout: post
title: "Sample CodeStar"
subtitle: "An AWS CodeStar Java Spring web service"
gh-repo: avnit/SampleCodeStar
gh-badge: [star, fork]
tags: [projects, java, aws, ci-cd]
comments: false
---

A Java Spring web service scaffolded by AWS CodeStar back in 2018 — a snapshot of what "click-to-provision CI/CD" looked like before it became table stakes.

## The context

AWS CodeStar was Amazon's answer to the "day zero" problem: pick a template (in this case, a Java Spring web service), and it would provision the whole delivery chain in one shot — a CodeCommit-style repo, a CodePipeline build-and-deploy pipeline, and the compute to run the service. This repo is what that generator produced: the Spring application skeleton plus the pipeline configuration that let a `git push` flow straight to a deployed endpoint.

## Why it's still here

Mostly as a time capsule. I was exploring managed CI/CD pipelines on AWS, and CodeStar was the fastest way to see the whole loop working end to end. AWS has since retired CodeStar as a standalone service, which makes this little repo a nice reminder of how quickly the "fully wired pipeline from a template" idea went from novelty to something every cloud now ships natively — the same pattern I now demo on Google Cloud with Cloud Build and Cloud Deploy.

The README is a single line, so there's not much more to document — the repo itself is the artifact.

**Language:** Java  
**Source code:** [github.com/avnit/SampleCodeStar](https://github.com/avnit/SampleCodeStar)
