---
layout: default
title: Home
nav_order: 1
description: "Pride yourself in well written documenation."
permalink: /
---


# Welcome to Robbie's Docs
{: .fs-9 }

This project is hosted on my GitHub and serves as the home for all documenation of my hobbies and interests.
{: .fs-6 .fw-300 }

---

## Latest updates

### Authelia

I use [Authelia](https://www.authelia.com/) to provide SSO authentication and authorization for my self-hosted web services that don't offer native web authentication. My Authelia is currently setup to only ask for a username and password. However, it also has the ability to incorporate Multi-factor Authentication (MFA) methods such as security keys, time-based one-time passwords, and mobile push notifications. For more information about how it works and how to configure your own Authelia using Unraid visit the full [page]({{ site.baseurl }}{% link Authelia.md %}).

---

### Nginx Proxy Manager

I am currently using [Nginx Proxy Manager](https://nginxproxymanager.com/guide/), with the help of Cloudfare's free DNS services, to help redirect my public domain name to my internal services on my network. By doing this, I can also utilize Let's Encrypt within Nginx to enable SSL encryption while accessing my services. Because my network is not exposed to the internet, this was more of a convenience project for me because now I don't have to remember the ip address and port numbers for each service... click [here]({{ site.baseurl }}{% link nginx.md %}) to visit the full page.