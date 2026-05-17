---
description: Complete the first YAPD setup and sign in for the first time.
icon: rocket
---

# First access and setup 🚀

The setup wizard creates the initial Pi-hole baseline, registers your first instances, chooses the login mode, and saves your display preferences.

## Before you begin 📋

Have these ready:

* the URL or IP address of each Pi-hole you want to manage;
* the Pi-hole password or application password for each instance;
* the instance you want to use as the **master** or **baseline**;
* whether your Pi-hole uses HTTP, HTTPS, a trusted certificate, or a self-signed certificate;
* the time zone you want YAPD to use for dates and reports.

## Complete the wizard 🪄

{% stepper %}
{% step %}
### Open YAPD 🌐

Open the YAPD address in your browser. With the default Compose install, direct access is usually `http://<server-ip>:48080`.
{% endstep %}

{% step %}
### Register Pi-holes 🧱

Add one or more Pi-hole URLs. For each row, provide an alias, protocol, host, port or path when needed, and the password or application password.
{% endstep %}

{% step %}
### Choose the master Pi-hole 👑

Select the Pi-hole that should become the official YAPD baseline. The baseline is the main reference for login and several sync comparisons.
{% endstep %}

{% step %}
### Choose the login mode 🔐

Choose whether operators sign in with the master Pi-hole password or with a dedicated YAPD password created during setup.
{% endstep %}

{% step %}
### Set layout preferences 🎛️

Choose the application language, time zone, theme, font, page width, navbar behavior, and sidebar style.
{% endstep %}

{% step %}
### Finish setup ✅

Review the choices and finish the wizard. YAPD validates the Pi-hole connections before saving the setup.
{% endstep %}
{% endstepper %}

## Login modes 🔑

| Mode | What it means | When to use it |
| --- | --- | --- |
| **Master Pi-hole password** | YAPD uses the official Pi-hole v6 login flow through the master Pi-hole. | You want the human login to follow the Pi-hole password. |
| **YAPD password** | YAPD stores a hashed product password for human login. | You want operators to sign in without using the Pi-hole password. |

{% hint style="info" %}
🔒 Pi-hole technical credentials are saved encrypted so the backend can operate registered instances. The password typed at login is not stored as a plain text login password.
{% endhint %}

## If setup fails 🧯

Check the most common causes:

* the Pi-hole URL includes the protocol twice;
* the host, port, or path is wrong;
* the password or application password is wrong;
* the backend cannot reach the Pi-hole from the Docker network;
* the Pi-hole uses a self-signed certificate and you did not explicitly allow it;
* the selected master Pi-hole was left incomplete.

For recovery steps, see [Common problems](../troubleshooting/common-problems.md).
