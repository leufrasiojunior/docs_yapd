---
description: Understand the product ideas that appear across the YAPD interface.
icon: lightbulb
---

# Core ideas 💡

YAPD uses a few recurring concepts across its screens.

## Instance 🧱

An **instance** is one Pi-hole registered in YAPD. Instances can be tested, edited, reauthenticated, included in sync, or removed from sync operations.

## Baseline 👑

The **baseline** is the primary Pi-hole reference. YAPD uses it as the main authority for several comparisons and sync flows. You can change the primary instance from the **Instances** screen.

## Scope 🎯

Some screens let you choose a scope:

* **All instances**: YAPD aggregates or compares all enabled instances.
* **Single instance**: YAPD shows only one Pi-hole.

## Sync 🔁

Sync copies selected data from a source to one or more target instances. It can apply to groups, clients, domains, ad-lists, configuration topics, or blocking state.

{% hint style="warning" %}
⚠️ Review the source and targets before confirming a sync. Sync is a real operation against your Pi-hole instances.
{% endhint %}

## Drift or divergence 🧭

Drift means one instance does not match the expected state or the selected source. YAPD highlights drift so you can review it before changing anything.

## Overview history 📊

Overview does not read only the live Pi-hole dashboard. It uses historical query data saved in YAPD's local database. You must import a closed day before Overview can rank domains, clients, upstreams, and statuses for that period.

## Notifications 🔔

Notifications are stored events and failures. They help you notice connection errors, sync failures, Overview import results, and other operational messages.

## Beta status 🚧

YAPD is still evolving. The product includes a BETA notice because it can operate directly on Pi-hole instances and because some workflows are still being refined.
