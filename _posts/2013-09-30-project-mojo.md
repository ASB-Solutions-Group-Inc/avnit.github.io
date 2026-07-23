---
layout: post
title: "Mojo"
subtitle: "Mojolicious — the Perl real-time web framework"
gh-repo: avnit/mojo
gh-badge: [star, fork]
tags: [projects, perl, web-dev]
comments: false
---

My fork of [mojolicious/mojo](https://github.com/mojolicious/mojo) — Mojolicious, the real-time web framework that gave Perl a genuinely modern web story. Forked back in 2013, when I was writing Perl for the web, and kept in my account for study; it's an unmodified copy of upstream.

## The concepts

Mojolicious came from the developers behind Catalyst, rebuilt around the latest web standards. Its signature trick is growth: you start with a single-file "Lite" prototype and grow it into a well-structured MVC application without a rewrite. It's a real-time framework at heart — WebSockets, long polling, and non-blocking I/O are first-class, not bolted on.

The stack is remarkably self-contained: a full HTTP and WebSocket client/server implementation with TLS, IPv6, and proxy support; a built-in non-blocking web server with hot deployment; JSON and HTML/XML parsers with CSS selector support; RESTful routing, templates, session management, and a testing framework — all in portable pure Perl with no hidden magic.

## How to use it

A complete web application is three lines:

```perl
use Mojolicious::Lite;

get '/' => {text => 'I ♥ Mojolicious!'};

app->start;
```

Save it to a file, run `morbo hello.pl`, and you have an app serving on port 3000.

## Installing it

One line, per the README:

```
curl -L https://cpanmin.us | perl - -M https://cpan.metacpan.org -n Mojolicious
```

Upstream remains one of the most popular distributions on CPAN, with excellent [documentation](https://docs.mojolicious.org) and a large ecosystem of extensions.

**Language:** Perl  
**Source code:** [github.com/avnit/mojo](https://github.com/avnit/mojo) · Upstream: [mojolicious/mojo](https://github.com/mojolicious/mojo)
