---
description: Use Overview Ranking to analyze historical domains, clients, upstreams, and statuses.
icon: bar-chart-3
---

# Ranking 🏆

Ranking turns imported Overview history into charts, tables, and clickable filters.

![YAPD Overview ranking](../.gitbook/assets/screenshots/overview.png)

## Choose saved dates 📆

The **Saved dates** controls define the period used by Ranking. Days with stored records are highlighted, so you can select only periods that actually exist in YAPD.

If there are no saved dates, import a closed day from [Period and coverage](overview-period-and-coverage.md).

## Apply filters 🔍

You can filter by:

* period;
* domain;
* client IP;
* grouping by hour or day.

Click **Apply** to reload the charts and tables. Click **Clear** to return to the broader period.

## What Ranking shows 📊

Ranking can show:

* total queries;
* allowed queries;
* blocked queries;
* block percentage;
* top domains;
* top clients;
* top upstreams;
* top statuses;
* status distribution;
* hours with the most access.

## Clickable drill-down 🖱️

Where useful, values in Ranking are clickable. Clicking a domain or client applies that value as a filter and refreshes the period.

This is useful when you notice a noisy domain or a client with unusual activity.

## Pi-hole totals can differ ⚖️

The native Pi-hole dashboard and YAPD can use slightly different time windows. YAPD evaluates the selected range through the full final minute, so totals may differ from the native Pi-hole view for the same apparent day.

{% hint style="info" %}
📌 Ranking uses only data stored locally by Overview imports. It is not a live query table.
{% endhint %}
