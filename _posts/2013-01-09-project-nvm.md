---
layout: post
title: "nvm — Node Version Manager"
subtitle: "Manage multiple active Node.js versions from the shell"
gh-repo: avnit/nvm
gh-badge: [star, fork]
tags: [projects, web-dev, learning]
comments: false
---

nvm is a version manager for Node.js — a simple POSIX-compliant bash script that lets you install and switch between multiple Node versions per user, invoked per shell. This is my fork of [nvm-sh/nvm](https://github.com/nvm-sh/nvm), kept in my account as a study reference and because it's a tool I use constantly across projects.

## The concepts

The core problem nvm solves is that different projects need different Node versions, and installing one globally is a recipe for pain. nvm installs each version under your home directory and switches the active one per shell session, so a single command changes which `node` and `npm` your terminal sees. It also supports `.nvmrc` files so a project can pin its expected version, LTS aliases, and migrating global packages when you install a new version.

## How to use it

The everyday workflow is a single command:

```sh
nvm install 20
nvm use 20
```

Drop a `.nvmrc` in a project directory and `nvm use` will pick up the pinned version automatically, which is handy for keeping a team on the same runtime.

## Running it

nvm is installed via its install script (curl or wget) or through a package manager, which adds the `nvm` function to your shell profile. See the upstream README for the current install command and shell-integration options.

**Language:** Shell  
**Source code:** [github.com/avnit/nvm](https://github.com/avnit/nvm)  
**Upstream:** [github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm)
