---
layout: post
title: "Workforce Identity"
subtitle: "Google Cloud Workforce Identity Federation without service account keys"
gh-repo: avnit/workforceidentity
gh-badge: [star, fork]
tags: [projects, google-cloud, security, iam]
comments: false
---

Configuration and examples for Google Cloud Workforce Identity Federation — letting users from an external identity provider access Google Cloud resources without minting service account keys or duplicating identities into Cloud Identity.

## The concepts

Workforce Identity Federation extends Google Cloud's IAM to trust an external IdP — Okta, Azure AD/Entra, or any OIDC or SAML 2.0 provider. Instead of syncing users or handing out long-lived credentials, the external IdP issues a token, Google's Security Token Service exchanges it for short-lived Google Cloud credentials, and IAM policies are written against the federated principal.

The security win is real: no service account keys to leak or rotate, session lifetimes you control, and attribute mappings that let you carry group membership and other claims from the IdP straight into IAM conditions. This is the pattern I recommend to customers in my day job as a security specialist, and this repo is where I keep working configurations for it.

## How to use it

The building blocks are a workforce pool, a pool provider (pointing at your IdP with attribute mappings), and IAM bindings that grant roles to `principalSet://` identities from the pool. Once configured, users sign in through the console federation URL or authenticate via `gcloud` with the pool's login configuration.

The repo doesn't carry a public README at the moment, so treat it as a working configuration reference rather than a polished tutorial.

**Source code:** [github.com/avnit/workforceidentity](https://github.com/avnit/workforceidentity)
