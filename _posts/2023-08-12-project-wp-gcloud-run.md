---
layout: post
title: "WordPress on Google Cloud Run"
subtitle: "Serverless WordPress — containerized, stateless, and deployed with two gcloud commands"
gh-repo: ASB-Solutions-Group-Inc/wp-gcloud-run
gh-badge: [star, fork]
tags: [projects, google-cloud, docker, serverless, web-dev]
comments: false
---

This repo (my fork of [peterkracik/wp-gcloud-run](https://github.com/peterkracik/wp-gcloud-run)) runs **WordPress on Google Cloud Run** — taking the world's most stateful CMS and making it behave in a serverless container platform.

## The concepts

Cloud Run containers are ephemeral, so the two stateful parts of WordPress have to move out of the container:

- **Media uploads** go to Google Cloud Storage via the [WP-Stateless plugin](https://wordpress.org/plugins/wp-stateless/), instead of the local filesystem
- **Configuration** comes from environment variables — `wp-config.php` reads database parameters from the environment rather than hard-coded values, with the database itself living outside on a MySQL host
- **Secrets** (like the GCS access token) come from Google Secret Manager at build time, not baked into the image

The image builds on the official PHP + Apache base with the MySQL and image-handling extensions WordPress needs.

## Deploying it

Two commands take it from source to a live site:

```bash
gcloud builds submit --tag gcr.io/PROJECT_NAME/IMAGE_NAME
gcloud run deploy wordpress --platform managed --image gcr.io/PROJECT_NAME/IMAGE_NAME \
  --set-env-vars DB_NAME=wordpress,DB_USER=root,DB_PASSWORD=...,DB_HOST=... --port 80
```

Environment variables can also come from a `.env.yaml` file or be set in the Cloud Run console. The result: WordPress that scales to zero when idle and scales out under load, with no VM to patch.

**Language:** PHP
**Source code:** [github.com/ASB-Solutions-Group-Inc/wp-gcloud-run](https://github.com/ASB-Solutions-Group-Inc/wp-gcloud-run) (fork of [peterkracik/wp-gcloud-run](https://github.com/peterkracik/wp-gcloud-run))
