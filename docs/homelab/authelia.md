---
layout: default
title: Authelia
parent: Homelab
nav_order: 5
---

# Authelia
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Details

I use [Authelia](https://www.authelia.com/) to provide SSO authentication and authorization for my self-hosted web services that don't offer native web authentication. Out of the box Authelia is configured to only ask for a username and password. However, it also has the ability to incorporate Multi-factor Authentication (MFA) methods such as security keys, time-based one-time passwords, and mobile push notifications. When I attempt to access a web service configured with Authelia, I am first greeted with this authentication page before I can access the service:

<img src="/assets/images/authelia_signon.png" width="350" height="349" alt="Authelia Sign-on">
{: .text-center }

Authelia runs as a simple docker container and functions between Nginx Proxy Manager (NPM) and the specific web service. When I access a web service that is configured to use Authelia (e.g., nodered.kamaji.org) I will first hit Nginx Proxy Manager which will redirect me to the Authelia sign-on page (hosted on auth.kamaji.org). After successfully authenticating, Authelia will authorize me by directing me to the service webpage. Otherwise, it will give me an error for incorrect username or password. For more information regarding how to configure Authelia with Nginx Proxy Manager, check out this [video from DB Tech](https://youtu.be/4UKOh3ssQSU).