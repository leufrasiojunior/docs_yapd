---
description: Register, test, reauthenticate, and manage Pi-hole instances.
icon: server
---

# Instances 🧱

Instances is where you manage the Pi-hole servers registered in YAPD.

![YAPD Instances](../.gitbook/assets/screenshots/instances.png)

## What you can do ✅

Use Instances to:

* register another Pi-hole;
* discover candidate Pi-hole URLs;
* test a saved connection;
* reauthenticate an expired session;
* include or exclude an instance from sync operations;
* edit connection settings;
* inspect operational information;
* make another instance the primary baseline.

## Register an instance ➕

You can register an instance manually or use guided discovery.

For manual registration, provide:

* name;
* protocol;
* host, port, and optional path;
* password or application password;
* certificate trust choice when needed.

## Trust choices 🔐

| Option | Use it when |
| --- | --- |
| Default trust | The Pi-hole certificate is trusted normally. |
| Explicit self-signed trust | You trust a local self-signed Pi-hole certificate. |
| Custom CA | You have a private CA certificate bundle. |

## Reauthenticate 🔑

Use **Reauthenticate** when:

* the Pi-hole session expired;
* the password changed;
* Notifications report a session failure;
* sync operations fail because the instance is unauthorized.

## Make primary 👑

Changing the primary instance updates the global YAPD baseline. The previous primary loses baseline status, and sync remains enabled on the new primary.

{% hint style="warning" %}
⚠️ Confirm the new primary carefully. The baseline affects comparisons and several sync flows.
{% endhint %}

## Error details 🧯

YAPD classifies common instance failures:

* invalid credentials;
* TLS or certificate failure;
* timeout;
* DNS error;
* connection refused;
* unexpected Pi-hole response;
* unclassified failure.

Open **More error details** for what to check next.
