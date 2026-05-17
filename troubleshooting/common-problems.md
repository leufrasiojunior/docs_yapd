---
description: Fix the most common YAPD installation and usage problems.
icon: life-ring
---

# Common problems 🧯

This page lists user-facing symptoms and what to check first.

## Login succeeds, then returns to login 🔁

Likely cause: cookie or origin mismatch.

Check:

* `WEB_ORIGIN` exactly matches the browser URL.
* `COOKIE_SECURE=true` when using HTTPS.
* `COOKIE_SECURE=false` only when using plain HTTP.
* The reverse proxy forwards the original protocol with `X-Forwarded-Proto`.

## YAPD cannot reach a Pi-hole 🌐

Check:

* the Pi-hole URL, protocol, port, and path;
* whether the YAPD container can reach that network;
* whether a firewall blocks the path;
* whether the Pi-hole password or application password changed;
* whether the instance uses a self-signed certificate.

Use **Instances > Test** after making changes.

## Self-signed certificate error 🔐

If the Pi-hole uses a local self-signed certificate, edit the instance and either:

* explicitly allow the self-signed certificate; or
* provide the custom CA bundle.

Only do this for Pi-hole endpoints you trust.

## Push notifications do not enable 🔔

Push needs a secure browser context.

Check:

* you are using HTTPS with a trusted certificate, or `localhost`;
* the browser has not blocked notifications for the site;
* your proxy does not cache `/notifications-sw.js`;
* the server has push configuration available.

## Overview shows no data 📊

Overview uses locally stored historical data. It does not automatically show live Pi-hole data unless a historical import has already saved that period.

Go to **Overview > Period and coverage**, choose a closed day, and request an import. Then watch **Overview > Jobs**.

## Overview cannot import today 📅

This is expected. Manual Overview imports are limited to one closed day. Choose yesterday or an earlier date.

## Queries Log live mode stops when disk mode is enabled 💿

This is expected. On-disk mode is slower and is meant for older Pi-hole data, so live updates are disabled.

## A sync only partially succeeded ⚠️

Open **Notifications** and review the failure. Then check the affected instance in **Instances**.

Common causes:

* one target instance was offline;
* a session expired;
* credentials changed;
* TLS validation failed;
* a Pi-hole response was different than expected.

## Container shows unhealthy 🐳

Check the container and logs:

```bash
docker compose ps
docker compose logs --tail=200 yapd
docker compose logs --tail=200 postgres
```

An external Pi-hole being unreachable should be treated as an instance problem, not as a reason to change Pi-hole data manually without checking YAPD logs and Notifications.
