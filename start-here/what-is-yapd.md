---
description: A friendly introduction to what YAPD does for Pi-hole users.
icon: house
---

# What is YAPD? 🧩

YAPD is a single dashboard for operating multiple Pi-hole v6+ instances without jumping between separate Pi-hole admin panels.

## Why it exists 💡

Running one Pi-hole is straightforward. Running several Pi-holes for a home, lab, VLAN setup, or small office can get messy:

* settings drift between instances;
* query activity is split across different dashboards;
* changes are easy to miss;
* manual sync can affect the wrong Pi-hole;
* temporary connection failures can be hard to understand.

YAPD gives you one place to watch, compare, and operate those instances.

## What YAPD is good at ✅

* 👀 **Daily visibility**: see live metrics and recent DNS activity.
* 📊 **Historical analysis**: use Overview to import and analyze stored query history.
* 🧱 **Pi-hole object management**: work with groups, clients, domains, and ad-lists.
* ⚙️ **Configuration review**: compare Pi-hole configuration topics and spot drift.
* 🔁 **Sync workflows**: copy selected state from a source instance to other targets.
* 🔔 **Operational awareness**: keep errors and important events visible in Notifications.

## What YAPD is not 🚫

YAPD is not a replacement for understanding what a Pi-hole change does. It helps you operate more safely, but changes such as deleting domains, changing groups, syncing configuration, or deleting Overview history can still affect your network.

{% hint style="warning" %}
🧪 YAPD is in development. Use care before applying changes to production Pi-hole instances.
{% endhint %}

## Where to go next 🧭

* New installation: [Install with Docker Compose](../administration/install-with-docker-compose.md)
* First login: [First access and setup](first-access-and-setup.md)
* Daily use: [Dashboard](../daily-use/dashboard.md)
* Historical analytics: [Overview](../daily-use/overview.md)
