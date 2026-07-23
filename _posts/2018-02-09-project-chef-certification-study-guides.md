---
layout: post
title: "Chef Certification Study Guides"
subtitle: "Study notes for the Basic Chef Fluency and Local Cookbook Development exams"
gh-repo: avnit/chef-certification-study-guides
gh-badge: [star, fork]
tags: [projects, learning, devops]
comments: false
---

This is my fork of a community set of study guides for Chef certification, turning one engineer's exam-prep notes into shareable guides for others working toward the same credentials. I keep it in my account as a reference for configuration-management concepts that carry over to the automation work in my homelab.

## The concepts

Chef is a configuration-management tool that models infrastructure as code through cookbooks and recipes, using a Ruby-based DSL to declare the desired state of a system. The guides here cover the ground the certification exams test: Basic Chef Fluency (the core vocabulary, resources, and workflow) and Local Cookbook Development (authoring, testing, and iterating on cookbooks locally). Framed as study-partner material, the repo is explicitly collaborative — the author invites issues and pull requests to improve the notes.

## How I use it

For me this is a learning resource rather than something to deploy. The declarative, idempotent thinking Chef teaches maps directly onto the Ansible and scripting I lean on to keep my lab reproducible, so the guides are a useful refresher even outside the Chef ecosystem itself. As a fork, the content mirrors the upstream author's notes.

**Source code:** [github.com/avnit/chef-certification-study-guides](https://github.com/avnit/chef-certification-study-guides)
