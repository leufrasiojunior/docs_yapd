---
description: Review devices detected by Pi-hole and manage client groups and tags.
icon: monitor-smartphone
---

# Clients 📱

Clients lists network devices detected by your Pi-hole instances and helps you organize them with groups, comments, and local tags.

## What you can do 👀

Use Clients to:

* search by client, IP, or MAC address;
* review where a device is visible;
* inspect first seen and last query information;
* edit local tags;
* hide selected tag categories from the table;
* manage group assignments;
* run manual client sync.

## Client details 🧾

The details view can show:

* client alias;
* MAC address;
* detected IPs;
* MAC vendor;
* preferred instance;
* visible instances;
* selected groups;
* comments;
* per-instance query counts.

## Tags 🏷️

Tags are local YAPD labels. Use them to organize devices without changing Pi-hole itself.

Examples:

* `iot`;
* `kids`;
* `guest`;
* `work`;
* `ignore`.

## Groups 👥

Client group assignments use baseline-backed group selection and then apply changes across available managed instances.

{% hint style="warning" %}
⚠️ Group changes can affect filtering behavior for the selected client. Confirm the selected groups before saving.
{% endhint %}

## Partial availability ⚠️

If some sync-enabled instances cannot be queried, YAPD shows the data returned by available instances and excludes unavailable ones from the current table.
