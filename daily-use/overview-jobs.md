---
description: Follow Overview imports, deletions, retries, cancellations, and job details.
icon: list-checks
---

# Jobs ⚙️

Jobs shows the background work created by Overview imports and deletions.

![YAPD Overview jobs](../.gitbook/assets/screenshots/overview.png)

## Why jobs exist 🧠

Historical imports can take time, especially across multiple Pi-hole instances. YAPD keeps this work in the background so Overview remains usable while the job runs.

## Job statuses 🚦

| Status | Meaning |
| --- | --- |
| **Queued** | Waiting to start. |
| **Running** | Import or deletion is in progress. |
| **Paused** | Execution paused after repeated failures. |
| **Cancelled** | Cancelled before it started. |
| **Success** | Completed with usable results. |
| **Partial** | Completed, but one or more instances had gaps or failures. |
| **Failure** | Finished without usable results. |

## Actions 🛠️

Depending on the status, you can:

* open the imported period in Ranking;
* view details;
* retry failed, paused, partial, or cancelled jobs;
* cancel queued jobs;
* delete old job records and linked Overview history.

{% hint style="warning" %}
⚠️ Deleting a successful, partial, paused, failed, or cancelled job can remove historical data linked to that job.
{% endhint %}

## Job details 🔎

The details modal includes:

* summary;
* scope;
* origin, such as manual or automatic import;
* period;
* expected and saved totals;
* attempts;
* progress percentage;
* primary failure reason;
* per-instance progress;
* timeline events.

Use this modal when an import fails or only partially completes.

## Common failure reasons 🧯

| Reason | What to check |
| --- | --- |
| **Timeout** | Instance availability, latency, or proxy behavior. |
| **Session error** | Reauthenticate the instance. |
| **Server unavailable** | Check whether the Pi-hole is online. |
| **Count mismatch** | Retry and compare the affected period. |
| **Unexpected failure** | Review details and YAPD logs. |
