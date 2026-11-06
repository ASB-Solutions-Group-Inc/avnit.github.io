---
layout: post
title: "Mantis"
subtitle: "Google's portable toolkit of security review skills for AI coding agents"
gh-repo: avnit/mantis
gh-badge: [star, fork]
tags: [projects, python, security, ai-agents, google-cloud]
comments: false
---

Mantis is a modular, stack-agnostic toolkit of security review skills that lets AI coding agents find, reproduce, and patch vulnerabilities. This is my fork of [google/mantis](https://github.com/google/mantis), kept as a reference for my own work on agent-driven code security.

## The concepts

The repo separates the method from the machinery that runs it:

- **`skills/`** is the method — skills an agent loads on demand, from threat modelling through research, review, patching, and reporting.
- **`reference/`** is an ADK harness that runs the method as a pipeline. It works as is, and it is meant to be adapted.
- **`action/`** is a GitHub Action that runs the harness over a pull request. Upstream marks it as untested end to end and says not to use it to gate merges yet.

Because the skills are plain, portable instructions, the same method can be loaded by different coding agents. The harness is one way to run it, not the only way.

## How to use it

```bash
cd reference && ./install.sh
gcloud auth application-default login          # if using Vertex AI
python3 scripts/configure.py --auto            # configure and auto-detect capabilities
python3 scripts/configure.py --test --probe    # preflight validation
./run.sh path/to/code                          # a file or a directory
./run.sh path/to/code --focus "look for IDOR"  # tell the planner what to hunt for
```

## Use it responsibly

The upstream README is blunt about this, and it should be:

- The suite generates and executes code autonomously. Run it only in an isolated, restricted environment — never on a machine with access to production systems, sensitive data, or internal networks.
- Models hallucinate findings and can write wrong patches. Every finding needs manual verification by someone who knows security before it is reported.
- Do not mass-file unverified, AI-generated reports to open-source maintainers.

A failed reproduction is not proof of a false positive, and a working reproducer is not proof the bug is exploitable everywhere.

**Language:** Python  
**Source code:** [github.com/avnit/mantis](https://github.com/avnit/mantis)  
**Upstream:** [github.com/google/mantis](https://github.com/google/mantis)
