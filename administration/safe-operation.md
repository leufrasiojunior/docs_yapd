---
description: Practical safety guidance for using YAPD against real Pi-hole instances.
icon: triangle-alert
---

# Safe operation 🛡️

YAPD can read and change real Pi-hole state, so review actions before confirming them.

## Good habits ✅

* 👀 Read the confirmation dialog before a delete or sync.
* 🎯 Confirm the selected source and target instances.
* 👑 Know which instance is the baseline.
* 🔁 Use sync intentionally, not as a blind "fix everything" button.
* 🔔 Check Notifications after operations that partially fail.
* 🧪 Test instance connections after changing Pi-hole passwords, URLs, certificates, or proxies.
* 💾 Keep backups outside YAPD.

## Actions that deserve extra care ⚠️

| Action | Why it matters |
| --- | --- |
| Delete groups, domains, or ad-lists | Removes data from managed instances. |
| Sync groups, domains, ad-lists, clients, or configuration | Copies selected state to target instances. |
| Change the primary instance | Changes the baseline reference used globally by YAPD. |
| Delete Overview periods | Removes locally stored historical data for that period. |
| Toggle blocking state | Can change DNS filtering behavior on one or more Pi-holes. |

## Certificates 🔐

If a Pi-hole uses a self-signed certificate, explicitly allow it only when you trust that instance and network path. If you have a private CA, prefer adding the custom CA instead of broadly allowing unknown certificates.

## Sessions 🔑

If an instance shows session errors, use **Reauthenticate** or edit the instance credential. Avoid assuming all instances share the same password unless you configured them that way.

## Beta warning 🚧

YAPD is still under active development. Use it first in a controlled environment when possible, then expand to more important Pi-hole instances after you understand the workflows.
