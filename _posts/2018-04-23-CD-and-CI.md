---
layout: post
published: false
title: "Continuous Integration and Continuous Delivery"
subtitle: "Notes on CI/CD pipelines and application lifecycle management"
tags: [devops, ci-cd, git]
comments: false
---

Working notes on Continuous Integration and Continuous Delivery: how code flows from a developer's commit through build, test, and deployment, and the goals a CI/CD pipeline should aim for.

## Continuous Integration (CI)

The basic CI flow:

```text
DEV -> Version Control -> CI Server -> Build -> Test -> Feedback to the developer
```

Version control is typically provided by the IT Ops team.

## Continuous Delivery (CD)

Once the build succeeds, the pipeline continues:

```text
Build is Success -> Staging -> Deploy to all the nodes on the production line
```

We can come up with various stages for the production line.

## Goals

- Automate everything
- Eliminate any manual tasks
- Store application and infrastructure code in version control
- Unify the application
- Perform end-to-end testing
- Version app and infrastructure code

## Understanding Application Lifecycle Management

The recommended version control system is Git (GitHub/Stash).

Before continuing, set up Git and run some basic commands:

1. Install Git locally and clone an existing repository from GitHub.
2. Make changes to the code.
3. `git commit` and `git push`.
4. Merge branches with `git merge`.

With version control and these fundamentals in place, the rest of the CI/CD pipeline builds naturally on top of them.
