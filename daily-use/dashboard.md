---
description: Use the Dashboard for a live consolidated view of your Pi-hole instances.
icon: gauge
---

# Dashboard 📈

Dashboard is the everyday live view for checking current Pi-hole activity across one or more registered instances.

![YAPD Dashboard](../.gitbook/assets/screenshots/dashboard.png)

## What you see 👀

The Dashboard shows:

* total queries;
* blocked queries;
* block percentage;
* total domains in ad-lists;
* query volume over the last 24 hours;
* top client activity over the last 24 hours;
* warnings when only part of the instances responded.

## Choose the scope 🎯

Use the **Scope** selector to switch between:

* **All instances**: combine data from every available operational instance.
* **One instance**: inspect a single Pi-hole.

{% hint style="info" %}
📌 Dashboard is a live operational screen. For historical analysis, use [Overview](overview.md).
{% endhint %}

## Partial data ⚠️

If one or more instances fail to respond, YAPD keeps the healthy data visible and shows a partial-data warning.

When this happens:

1. Open **Instances**.
2. Test the failed instance.
3. Reauthenticate it if the session expired.
4. Check **Notifications** for a clearer failure reason.

## When to use Dashboard ✅

Use Dashboard when you want to know what is happening now:

* after changing a blocking rule;
* after adding or removing an ad-list;
* when a client seems unusually active;
* when you want a quick health check before doing a sync.
