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

I use [Authelia](https://www.authelia.com/) to provide SSO authentication and authorization for my self-hosted web services that don't offer native web authentication. My Authelia is currently setup to only ask for a username and password. However, it also has the ability to incorporate Multi-factor Authentication (MFA) methods such as security keys, time-based one-time passwords, and mobile push notifications. For more information regarding how to configure Authelia with Nginx Proxy Manager, check out this [video from DB Tech](https://youtu.be/4UKOh3ssQSU).

Authelia works by sitting between Nginx Proxy Manager (NPM) and the web services themselves. Before NPM forwards my session to its destination address and port, it will first redirect me to the Authelia sign-on. After I have successfully authenticated, it will authorize me by redirecting me back to the original 

---

## Screenshots

<div class="code-example">
<img src="/assets/images/authelia_signon.png" alt="Authelia Sign-on"> 
</div>
