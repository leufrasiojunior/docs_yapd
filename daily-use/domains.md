---
description: Manage exact domains and regex rules across Pi-hole instances.
icon: globe
---

# Domains 🌐

Domains lets you manage exact domain entries and preset regex rules across your Pi-hole instances.

![YAPD Domains](../.gitbook/assets/screenshots/domains.png)

## Domain types 🧩

YAPD supports:

* exact allow entries;
* exact block entries;
* regex allow entries;
* regex block entries;
* preset regex patterns for common use cases.

## Create a domain ➕

When creating a domain, choose:

* domain or regex text;
* filter type;
* comment;
* assigned groups.

YAPD attempts to replicate the new entry across managed instances.

## Table actions 🛠️

From the table you can:

* search by domain or comment;
* refresh the view;
* sync domains;
* enable or disable entries;
* open details;
* edit groups and comments;
* remove one or more domains;
* export or import CSV.

## Sync pending 🔁

If a domain exists on some instances but not others, use the sync dialog to choose a source and targets.

{% hint style="warning" %}
⚠️ Removing a domain removes it from every managed instance selected by the operation.
{% endhint %}
