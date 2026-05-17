---
description: Keep YAPD and its data recoverable during regular operation.
icon: database-backup
---

# Backup and maintenance 💾

YAPD stores its own data in PostgreSQL, including setup state, registered instances, notifications, preferences, and locally imported Overview history.

## What to back up 🧳

Back up:

* the PostgreSQL volume used by YAPD;
* your edited `compose.yml`;
* any external reverse proxy configuration;
* notes about your Pi-hole URLs, certificate choices, and login mode.

{% hint style="info" %}
📌 YAPD does not replace Pi-hole backups. Continue backing up your Pi-hole instances separately.
{% endhint %}

## Before risky changes ✅

Create a backup before:

* changing the production Compose file;
* moving YAPD to another server;
* replacing secrets;
* bulk syncing configuration;
* deleting large historical Overview periods.

## Maintenance checks 🧰

Use these checks during normal operation:

```bash
docker compose ps
docker compose logs --tail=200 yapd
docker compose logs --tail=200 postgres
```

Then inspect the UI:

* **Instances**: look for expired sessions or failed validation.
* **Notifications**: mark expected events as read and review failures.
* **Overview > Jobs**: check failed, paused, or partial jobs.
* **Configuration**: review drift before syncing.

## Updating YAPD ⬆️

A normal update usually means pulling a newer image and restarting:

```bash
docker compose pull
docker compose up -d
```

After the update, open YAPD and verify:

* the login still works;
* the baseline is still correct;
* registered instances still test successfully;
* Overview jobs and Notifications load.
