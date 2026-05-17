---
description: Known rough edges and current limitations to keep in mind.
icon: bug
---

# Known issues 🐞

YAPD is active, early software. These are known limitations or behaviors worth remembering.

## Intermittent Pi-hole reachability 🌐

YAPD can sometimes lose connection to a Pi-hole instance, fail to locate it, or briefly show it as unreachable. In some cases the instance recovers shortly after without a manual restart.

What to do:

* wait briefly and refresh the affected screen;
* check **Instances** for the last error;
* test the instance connection;
* review **Notifications** for the clearer failure reason;
* collect logs if the issue repeats.

## Overview depends on imported history 📊

Overview can feel empty after a fresh install because it only analyzes data saved in YAPD's local database. Import a closed day before expecting rankings or charts.

## On-disk query mode is slower 💿

Queries Log can request older data from Pi-hole's on-disk database, but this mode is slower and disables live updates.

## Push notifications require real HTTPS 🔔

Push notifications usually do not work through direct HTTP access by IP address or through self-signed public browser certificates. Use a trusted HTTPS domain.

## Some workflows are still evolving 🚧

YAPD's roadmap includes stronger backup, realtime operation visibility, improved health diagnostics, and future parental-control features. Treat visible beta warnings seriously when operating production Pi-hole instances.
