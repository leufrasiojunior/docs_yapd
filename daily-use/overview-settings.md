---
description: Schedule recurring Overview imports for closed days.
icon: settings
---

# Overview settings ⏰

Overview settings lets you create automatic import rules that queue historical collection jobs.

![YAPD Overview settings](../.gitbook/assets/screenshots/overview.png)

## What automatic import does 🤖

An automatic rule schedules Overview collection. The rule decides when to run, but the imported window remains the complete previous closed day in the application-configured time zone.

Example: a daily rule at `03:00` imports the completed `d-1` day.

## Rule fields 📝

| Field | Meaning |
| --- | --- |
| **Name** | Friendly name for the rule. |
| **Enabled** | Disabled rules stay saved but do not schedule jobs. |
| **Instance** | Choose all instances or one specific instance. |
| **Preset** | Use daily or hourly presets, or provide a custom cron expression. |
| **Cron** | The final schedule expression used by the rule. |

## Presets ⚡

Available presets include:

* every day at `03:00`;
* every day at `00:00`;
* every day at `06:00`;
* every hour;
* custom expression.

{% hint style="info" %}
📌 Automatic imports appear in [Jobs](overview-jobs.md), just like manual imports.
{% endhint %}

## When to use it ✅

Use automatic imports when you want Overview rankings to be ready every day without manually importing the previous day.
