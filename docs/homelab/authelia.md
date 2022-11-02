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

I use [Authelia](https://www.authelia.com/) to provide SSO authentication and authorization for my self-hosted web services that don't offer native web authentication. This is accomplished by sitting between my Nginx Proxy Manager (NPM) and the web services themselves. Before NPM forwards my session to its destination address and port, it will first redirect me to the Authelia sign-on page which looks like this:

<img src="/assets/images/authelia_signon_small.png" alt="Authelia Sign-on">
{: .text-center }

Currently, I only have Authelia setup to ask for a username and password. However, Authelia also has the ability to incorporate Multi-factor Authentication (MFA) methods such as security keys, time-based one-time passwords, and mobile push notifications. For more information regarding how to configure Authelia with Nginx Proxy Manager, check out this [video from DB Tech](https://youtu.be/4UKOh3ssQSU).