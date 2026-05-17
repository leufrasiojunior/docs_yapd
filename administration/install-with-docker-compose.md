---
description: Install YAPD with the production Docker Compose file.
icon: download
---

# Install with Docker Compose 🐳

Docker Compose is the recommended way to run YAPD for normal self-hosted use.

## What you will run 📦

The production Compose file starts:

* a **YAPD app** container with the web interface, API, and internal Nginx;
* a **PostgreSQL** container for YAPD data;
* a private Docker network;
* a persistent Postgres volume.

The default published ports are:

| Port | Purpose |
| --- | --- |
| `48080` | HTTP access to YAPD |
| `48443` | internal HTTPS access with a self-signed certificate |

{% hint style="info" %}
🌐 If you use an external reverse proxy, point it to `http://<server-ip>:48080` and let the proxy handle the public HTTPS certificate.
{% endhint %}

## Quick install ⚡

{% stepper %}
{% step %}
### Download the Compose file 📥

```bash
curl -O https://raw.githubusercontent.com/leufrasiojunior/yadp/main/compose.yml
```
{% endstep %}

{% step %}
### Edit the required values ✏️

Open `compose.yml` and change at least:

* `postgres_password`
* `session_secret`
* `app_encryption_key`
* `web_origin`

Use values that are unique to your installation.
{% endstep %}

{% step %}
### Start YAPD ▶️

```bash
docker compose up -d
```
{% endstep %}

{% step %}
### Open the app 🌐

Open:

```text
http://<server-ip>:48080
```

Then complete [First access and setup](../start-here/first-access-and-setup.md).
{% endstep %}
{% endstepper %}

## Important values 🔐

| Value | What to set |
| --- | --- |
| `postgres_password` | A strong Postgres password. |
| `session_secret` | A long random secret for YAPD sessions. |
| `app_encryption_key` | A long random secret used for encrypted application data. |
| `web_origin` | The exact browser URL used to open YAPD, such as `https://yapd.example.com`. |
| `cookie_secure` | Use `true` when the browser opens YAPD over HTTPS. Use `false` only for plain HTTP access. |

{% hint style="danger" %}
🚫 Do not reuse the example secrets from the Compose file in a real installation.
{% endhint %}

## Basic commands 🧰

| Task | Command |
| --- | --- |
| Start | `docker compose up -d` |
| Stop | `docker compose down` |
| View app logs | `docker compose logs --tail=200 yapd` |
| View database logs | `docker compose logs --tail=200 postgres` |
| Check containers | `docker compose ps` |

## After installation ✅

Continue with:

* [First access and setup](../start-here/first-access-and-setup.md)
* [Reverse proxy and HTTPS](reverse-proxy-and-https.md)
* [Safe operation](safe-operation.md)
