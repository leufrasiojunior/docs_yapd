---
description: Put YAPD behind a reverse proxy and keep browser security working.
icon: shield-check
---

# Reverse proxy and HTTPS 🔐

Use a reverse proxy when you want a friendly domain, a trusted HTTPS certificate, and browser features such as push notifications.

## Recommended path 🌐

Use this flow:

```text
Browser -> https://yapd.example.com -> reverse proxy -> http://YAPD_HOST:48080
```

The public browser URL should use HTTPS. The private hop from your proxy to YAPD can use HTTP on port `48080`.

{% hint style="warning" %}
⚠️ Avoid using `https://YAPD_HOST:48443` as the normal upstream. That port uses YAPD's internal self-signed certificate and usually creates certificate trust problems in proxies.
{% endhint %}

## Required settings ⚙️

Set these values in your Compose file:

```yaml
WEB_ORIGIN: "https://yapd.example.com"
COOKIE_SECURE: "true"
NEXT_PUBLIC_API_BASE_URL: /api
INTERNAL_API_BASE_URL: http://127.0.0.1:3001/api
```

`WEB_ORIGIN` must exactly match the URL users type in the browser.

## Nginx example 🧱

```nginx
server {
    listen 443 ssl;
    server_name yapd.example.com;

    ssl_certificate /path/to/fullchain.pem;
    ssl_certificate_key /path/to/privkey.pem;

    location / {
        proxy_pass http://YAPD_HOST:48080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_read_timeout 86400;
    }
}
```

## Caddy example ⚡

```caddy
yapd.example.com {
    reverse_proxy http://YAPD_HOST:48080 {
        header_up Host {host}
        header_up X-Real-IP {remote_host}
        header_up X-Forwarded-For {remote_host}
        header_up X-Forwarded-Proto {scheme}
    }
}
```

## Nginx Proxy Manager checklist ✅

1. Create a new **Proxy Host**.
2. Set **Domain Names** to your YAPD domain.
3. Set **Scheme** to `http`.
4. Set **Forward Hostname/IP** to the YAPD host.
5. Set **Forward Port** to `48080`.
6. Enable **Websockets Support**.
7. Add or request a trusted SSL certificate.
8. Enable **Force SSL** after the domain works.
9. Keep **Cache Assets** disabled while testing push notifications.

## Push notifications 🔔

Browser push needs HTTPS with a trusted public certificate. A self-signed certificate usually blocks the service worker and prevents push from working.

If your proxy caches assets, add a no-cache rule for:

```text
/notifications-sw.js
```

See [Notifications](../daily-use/notifications.md) for user-facing behavior.
