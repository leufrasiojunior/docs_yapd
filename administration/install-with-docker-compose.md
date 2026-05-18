---
description: Choose between full Compose, external database, copied file, or cloned repository installation.
icon: download
---

# Install with Docker Compose 🐳

Docker Compose is the recommended way to run YAPD for normal self-hosted use.

Use one of the tabs below depending on your database model and how you prefer to start the installation.

## What you will run 📦

The production Compose setup can run in two ways:

* **Full Compose**: starts the **YAPD app** container and a dedicated **PostgreSQL** container.
* **External database**: starts only the **YAPD app** container and connects to an existing external PostgreSQL server.

In both cases, the YAPD container includes the web interface, API, and internal Nginx.

The default published ports are:

| Port | Purpose |
| --- | --- |
| `48080` | HTTP access to YAPD |
| `48443` | internal HTTPS access with a self-signed certificate |

{% hint style="info" %}
🌐 If you use an external reverse proxy, point it to `http://<server-ip>:48080` and let the proxy handle the public HTTPS certificate.
{% endhint %}

## Installation methods ⚡

{% tabs %}
{% tab title="Full Compose" %}
Use this option when YAPD should also create and manage the PostgreSQL container.

Create a `compose.yml` file with this content:

```yaml
services:
  postgres:
    image: postgres:16-alpine
    restart: unless-stopped
    environment:
      - POSTGRES_DB=yapd
      - POSTGRES_USER=yapd
      - POSTGRES_PASSWORD=change-this-password
    volumes:
      - yapd-prod-postgres-data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -h localhost -U \"$${POSTGRES_USER}\" -d \"$${POSTGRES_DB}\""]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 10s

  yapd:
    image: leufrasiojunior/yapd:latest
    restart: unless-stopped
    depends_on:
      postgres:
        condition: service_healthy
    ports:
      - "48080:80"
      - "48443:443"
    environment:
      - NODE_ENV=production
      - PORT=3000
      - HOSTNAME=0.0.0.0
      - API_HOST=0.0.0.0
      - API_PORT=3001
      # Set this to the exact browser URL, for example https://yapd.example.com.
      - WEB_ORIGIN=https://example.domain.com
      - API_BASE_URL=/api
      - INTERNAL_API_BASE_URL=http://127.0.0.1:3001/api
      - NEXT_PUBLIC_API_BASE_URL=/api
      - YAPD_POSTGRES_HOST=postgres
      - YAPD_POSTGRES_DB=yapd
      - YAPD_POSTGRES_USER=yapd
      # Keep this value equal to POSTGRES_PASSWORD above.
      - YAPD_POSTGRES_PASSWORD=change-this-password
      # Replace these secrets before starting the stack.
      - SESSION_SECRET=change-this-session-secret
      - APP_ENCRYPTION_KEY=change-this-encryption-key
      # Push notifications require a trusted HTTPS browser origin or localhost.
      - WEB_PUSH_VAPID_SUBJECT=mailto:admin@yapd.local
      - COOKIE_SECURE=true
      - SWAGGER_ENABLED=false
      - YAPD_DB_MIGRATION_MAX_ATTEMPTS=30
      - YAPD_DB_MIGRATION_RETRY_DELAY_SECONDS=2
      - YAPD_API_READY_MAX_ATTEMPTS=30
      - YAPD_API_READY_RETRY_DELAY_SECONDS=1
    command:
      - bash
      - -c
      - |
        export DATABASE_URL="postgresql://$${YAPD_POSTGRES_USER}:$${YAPD_POSTGRES_PASSWORD}@$${YAPD_POSTGRES_HOST}:5432/$${YAPD_POSTGRES_DB}?schema=public"
        exec bash ./scripts/start-app-container.sh
    healthcheck:
      test:
        [
          "CMD-SHELL",
          "wget -qO- http://127.0.0.1:80/healthz >/dev/null 2>&1 && wget -qO- http://127.0.0.1:3001/api/health >/dev/null 2>&1 || exit 1"
        ]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 45s

volumes:
  yapd-prod-postgres-data:
```

Before starting, change `POSTGRES_PASSWORD`, `YAPD_POSTGRES_PASSWORD`, `SESSION_SECRET`, `APP_ENCRYPTION_KEY`, and `WEB_ORIGIN`. The two Postgres password values must match.

```bash
docker compose up -d
```
{% endtab %}

{% tab title="External DB" %}
Use this option when you already have an external PostgreSQL server and only want to run the YAPD container.

Create a `compose.yml` file with this content:

```yaml
services:
  yapd:
    image: leufrasiojunior/yapd:latest
    restart: unless-stopped
    ports:
      - "48080:80"
      - "48443:443"
    environment:
      - NODE_ENV=production
      - PORT=3000
      - HOSTNAME=0.0.0.0
      - API_HOST=0.0.0.0
      - API_PORT=3001
      # Set this to the exact browser URL, for example https://yapd.example.com.
      - WEB_ORIGIN=https://example.domain.com
      - API_BASE_URL=/api
      - INTERNAL_API_BASE_URL=http://127.0.0.1:3001/api
      - NEXT_PUBLIC_API_BASE_URL=/api
      # Set these values for your external PostgreSQL server.
      - YAPD_POSTGRES_HOST=postgres.example.internal
      - YAPD_POSTGRES_DB=yapd
      - YAPD_POSTGRES_USER=yapd
      - YAPD_POSTGRES_PASSWORD=change-this-password
      # Replace these secrets before starting the stack.
      - SESSION_SECRET=change-this-session-secret
      - APP_ENCRYPTION_KEY=change-this-encryption-key
      # Push notifications require a trusted HTTPS browser origin or localhost.
      - WEB_PUSH_VAPID_SUBJECT=mailto:admin@yapd.local
      - COOKIE_SECURE=true
      - SWAGGER_ENABLED=false
      - YAPD_DB_MIGRATION_MAX_ATTEMPTS=30
      - YAPD_DB_MIGRATION_RETRY_DELAY_SECONDS=2
      - YAPD_API_READY_MAX_ATTEMPTS=30
      - YAPD_API_READY_RETRY_DELAY_SECONDS=1
    command:
      - bash
      - -c
      - |
        export DATABASE_URL="postgresql://$${YAPD_POSTGRES_USER}:$${YAPD_POSTGRES_PASSWORD}@$${YAPD_POSTGRES_HOST}:5432/$${YAPD_POSTGRES_DB}?schema=public"
        exec bash ./scripts/start-app-container.sh
    healthcheck:
      test:
        [
          "CMD-SHELL",
          "wget -qO- http://127.0.0.1:80/healthz >/dev/null 2>&1 && wget -qO- http://127.0.0.1:3001/api/health >/dev/null 2>&1 || exit 1"
        ]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 45s
```

The external PostgreSQL server must be reachable from the YAPD container on port `5432`. If your database uses another port, edit the port inside the `DATABASE_URL` built in the `command` block.

{% hint style="warning" %}
Create the database manually before starting YAPD. Its name must match `YAPD_POSTGRES_DB`, and `YAPD_POSTGRES_USER` must have permission to create and update tables in that database.
{% endhint %}

```bash
docker compose up -d
```
{% endtab %}

{% tab title="Copy the Compose file" %}
Use this option when you want to download the official repository file and edit it locally.

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

* `POSTGRES_PASSWORD`
* `YAPD_POSTGRES_PASSWORD`
* `SESSION_SECRET`
* `APP_ENCRYPTION_KEY`
* `WEB_ORIGIN`

The two Postgres password values must match.
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
{% endtab %}

{% tab title="Clone the repository" %}
Use this option when you want to keep the Compose file together with a local repository checkout.

{% stepper %}
{% step %}
### Clone the repository 📦

```bash
git clone https://github.com/leufrasiojunior/yadp.git
cd yadp
```
{% endstep %}

{% step %}
### Edit the Compose file ✏️

Open `compose.yml` and change `POSTGRES_PASSWORD`, `YAPD_POSTGRES_PASSWORD`, `SESSION_SECRET`, `APP_ENCRYPTION_KEY`, and `WEB_ORIGIN`.
{% endstep %}

{% step %}
### Start YAPD ▶️

```bash
docker compose -f compose.yml up -d
```
{% endstep %}

{% step %}
### Open the app 🌐

Open `http://<server-ip>:48080` and complete [First access and setup](../start-here/first-access-and-setup.md).
{% endstep %}
{% endstepper %}
{% endtab %}
{% endtabs %}

## Important values 🔐

| Value | What to set |
| --- | --- |
| `POSTGRES_PASSWORD` | Strong password for the Postgres container in the full Compose setup. |
| `YAPD_POSTGRES_HOST` | PostgreSQL host used by YAPD. In the full Compose setup, keep `postgres`. |
| `YAPD_POSTGRES_DB` | Database name used by YAPD. |
| `YAPD_POSTGRES_USER` | Database user used by YAPD. |
| `YAPD_POSTGRES_PASSWORD` | Database password used by YAPD. In the full Compose setup, it must match `POSTGRES_PASSWORD`. |
| `SESSION_SECRET` | A long random secret for YAPD sessions. |
| `APP_ENCRYPTION_KEY` | A long random secret used for encrypted application data. |
| `WEB_ORIGIN` | The exact browser URL used to open YAPD, such as `https://yapd.example.com`. |
| `COOKIE_SECURE` | Use `true` when the browser opens YAPD over HTTPS. Use `false` only for plain HTTP access. |
| `WEB_PUSH_VAPID_SUBJECT` | Contact address used by the push notification service, usually in the `mailto:admin@yourdomain.com` format. |

{% hint style="danger" %}
🚫 Do not reuse the example secrets from the Compose file in a real installation.
{% endhint %}

## Basic commands 🧰

| Task | Command |
| --- | --- |
| Start | `docker compose up -d` |
| Stop | `docker compose down` |
| View app logs | `docker compose logs --tail=200 yapd` |
| View database logs in the full Compose setup | `docker compose logs --tail=200 postgres` |
| Check containers | `docker compose ps` |

## After installation ✅

Continue with:

* [First access and setup](../start-here/first-access-and-setup.md)
* [Reverse proxy and HTTPS](reverse-proxy-and-https.md)
* [Safe operation](safe-operation.md)
