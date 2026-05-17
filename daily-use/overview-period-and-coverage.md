---
description: Import closed days and understand available Overview coverage.
icon: calendar-days
---

# Period and coverage 📅

Period and coverage is where you choose a closed day, request historical import, delete stored history, and see what Overview data is available.

![YAPD Overview period and coverage](../.gitbook/assets/screenshots/overview.png)

## Pick a day 🎯

Use **Date**, **From**, and **Until** to choose the period.

For manual imports:

* the period must stay inside one calendar day;
* the day must be closed;
* the current date cannot be imported;
* the time fields can still be adjusted inside that selected day.

## Request import 📥

Click **Request import** to queue a background job.

After queueing:

1. YAPD creates a job.
2. The screen remains usable.
3. Progress appears in **Overview > Jobs**.
4. Notifications are created when the import succeeds, partially succeeds, or fails.

## Delete period 🗑️

Use **Delete period** when you want to remove stored Overview history for the selected period.

{% hint style="warning" %}
⚠️ Deleting an Overview period removes locally stored historical rows. It does not delete data from Pi-hole, but Ranking will no longer have that period until you import it again.
{% endhint %}

## Available coverage 🧾

Coverage tells you what YAPD already has saved:

* stored query count;
* earliest and latest stored records;
* completed or partial stored periods;
* periods close to expiration;
* coverage that can be renewed.

## Renew coverage 🔄

When a stored period is close to expiring, YAPD can renew it for 30 more days without fetching the data again.

Use **Renew +30 days** when you still need that historical period available for future Ranking analysis.
