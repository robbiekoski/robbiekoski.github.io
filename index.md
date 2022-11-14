---
layout: default
title: Home
nav_order: 1
description: "Pride yourself in well written documenation."
permalink: /
---


# Welcome!
{: .fs-9 }

This project is hosted on my GitHub and serves as the home for all documenation of my hobbies and interests.
{: .fs-6 .fw-300 }

---

## Latest updates

### Home Assistant

One of the main reasons for creating my homelab in the first place was because of my interest in home automation. I first got the idea of creating a smart home a few years ago when my friend explained to me what [Home Assistant](https://www.home-assistant.io/) was and how he incorporated it into his daily life. From customizing your own dashboard, to creating convenient automations, and even integrating different wireless device protocols enabling them to communicate together... click [here]({{ site.baseurl }}{% link docs/homelab/homeassistant.md %}) to read more.

---

### Authelia

I use [Authelia](https://www.authelia.com/) to provide SSO authentication and authorization for my self-hosted web services that don't offer native web authentication. My Authelia is currently setup to only ask for a username and password. However, it also has the ability to incorporate Multi-factor Authentication (MFA) methods such as security keys, time-based one-time passwords, and mobile push notifications... click [here]({{ site.baseurl }}{% link docs/homelab/authelia.md %}) to read more.

---

### Nginx Proxy Manager

I am currently using [Nginx Proxy Manager](https://nginxproxymanager.com/guide/), with the help of Cloudfare's free DNS services, to help forward my public domain name to my internal services on my network. By doing this, I can also utilize Let's Encrypt within Nginx to enable SSL encryption while accessing my services. Because my network is not exposed to the internet, this was more of a convenience project for me because now I don't have to remember the ip address and port numbers for each service... click [here]({{ site.baseurl }}{% link docs/homelab/nginx.md %}) to read more.

---

### Heimdall

[Heimdall](https://heimdall.site/) serves as my primary dashboard that contains the links to all of my self-hosted services. The ability to be quickly deployed as a docker container, options for personalization, and native icon support for many applications makes heimdall the perfect candidate as a homelab dashboard... click [here]({{ site.baseurl }}{% link docs/homelab/heimdall.md %}) to read more.