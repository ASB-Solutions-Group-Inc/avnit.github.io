---
layout: post
title: "Python Flask Ext API Example"
subtitle: "OAuth2 against the Airthings API from a small Flask app"
gh-repo: avnit/python-flask-ext-api-example
gh-badge: [star, fork]
tags: [projects, python, iot, api]
comments: false
---

My fork of [Airthings/python-flask-ext-api-example](https://github.com/Airthings/python-flask-ext-api-example), Airthings' official sample showing how to access their air-quality sensor API from a simple Flask web app using the `requests-oauthlib` library. I keep it in my account as a reference for talking to the Airthings for Business API — air quality monitoring is a natural fit for a homelab that already runs Home Assistant.

## The concepts

The sample demonstrates the OAuth2 Authorization Grant flow end to end. An `AirthingsAccount` class wraps the three steps: initialize with your client ID, client secret, and redirect URI; call `get_authorization()` to get the login URL that redirects back to your app; then feed the redirect URL to `get_access_token()` to exchange the authorization code for a token. From there the Flask routes make authenticated `GET` requests against the API and render the JSON results.

Upstream is explicit that this is a teaching example, not production code — and it makes the right point about never embedding client secrets directly in the web app.

## Running it

Straight from the README:

```
git clone https://github.com/Airthings/python-flask-ext-api-example
cd python-flask-ext-api-example
pip install -r requirements.txt
python app.py
```

You'll need API credentials (client ID, secret, redirect URI) from the Airthings accounts dashboard before anything works.

**Source code:** [github.com/avnit/python-flask-ext-api-example](https://github.com/avnit/python-flask-ext-api-example) · Upstream: [Airthings/python-flask-ext-api-example](https://github.com/Airthings/python-flask-ext-api-example)
