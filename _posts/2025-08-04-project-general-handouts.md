---
layout: post
title: "General Handouts"
subtitle: "LaTeX source for course handouts, built reproducibly with latexmk"
gh-repo: avnit/General_Handouts
gh-badge: [star, fork]
tags: [projects, learning, latex]
comments: false
---

My fork of [scpd-proed/General_Handouts](https://github.com/scpd-proed/General_Handouts), a repository of LaTeX source for compiling course handouts (not the assignment handouts themselves). I kept it in my account while taking the associated coursework.

## The concepts

The repo's one hard rule is reproducible builds: every document must compile with nothing more than a bare `latexmk` command. Each handout lives in its own subdirectory with a `latexmkrc` settings file that declares the root `.tex` file, the output name, and the engine options — so any member of the course staff can build any document identically without knowing its quirks. A typical config sets `pdf_mode`, elevates warnings to errors for cleaner sources, and runs `pdflatex` in halt-on-error batch mode.

## How to use it

From any handout's directory:

```bash
latexmk         # build the PDF
latexmk -pvc    # rebuild continuously as you edit
latexmk -c      # clean auxiliary files
```

It's a small repo, but the pattern — one deterministic build command per document, with all the per-document configuration pushed into `latexmkrc` — is a nice piece of build hygiene that applies well beyond LaTeX.

**Source code:** [github.com/avnit/General_Handouts](https://github.com/avnit/General_Handouts)
**Upstream:** [github.com/scpd-proed/General_Handouts](https://github.com/scpd-proed/General_Handouts)
