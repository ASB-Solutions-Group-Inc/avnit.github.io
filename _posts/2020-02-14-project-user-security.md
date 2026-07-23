---
layout: post
title: "User Security"
subtitle: "A Spring Boot user microservice with OAuth 2 and Spring Security"
gh-repo: avnit/user-security
gh-badge: [star, fork]
tags: [projects, java, security]
comments: false
---

User Security is a Spring Boot boilerplate for a user microservice, built around Spring Security and OAuth 2 — a friendly starting point for the authentication and authorization layer that so many Java services need. It bundles a few related experiments, including a Firestore-backed Cloud Function and a Groovy/Gradle rewrite of the same project.

## The concepts

The project leans on the Spring ecosystem to cover the security fundamentals: Spring Boot for the service scaffolding, Spring Security and Spring OAuth 2 for authentication and token handling, and Spring Data JPA for persistence. It also wires in the `specification-arg-resolver` library so API consumers can filter query results cleanly, and it includes an optional RSA signature-check helper for validating signed requests. Swagger UI is exposed so the endpoints are browsable and testable out of the box.

## How to use it

You import the provided `init.sql`, configure `application.yml`, and hit the API through Swagger. The app defaults to port 8085. It is meant as boilerplate you clone and adapt rather than a finished product.

## Running it

```
mvn package
java -jar target/users-0.0.1-SNAPSHOT.jar
```

There is also a Dockerfile:

```
docker build -t test .
docker run -it test:latest
```

Swagger UI then lives at `localhost:8085/swagger-ui.html`.

**Language:** Java
**Source code:** [github.com/avnit/user-security](https://github.com/avnit/user-security)
