---
layout: default
title: Overview
parent: Homelab
---

# Overview
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## pfSense

When I started planning for my home network I knew that I wanted to incorporate a dedicated, easily manageable, open source firewall. There were a couple of options that I was choosing from, however, my friend recommended that I check out [pfSense](https://www.pfsense.org/). So I did, and never looked back. Currently running on a fanless Mini PC from [Qotom](https://www.qotom.net/), my pfSense box serves as my router, firewall, DHCP server, and more that is all easily configurable within a convenient web-based dashboard.

---

## Unraid


### Background
Before I eventually decided to use [Unraid](https://unraid.net/), I was running Proxmox to create and manage my virtual machines and containers. It was very helpful in initially learning the basics of virtualization, however, I felt myself wanting more. In addition, knowing that I wanted to build myself a NAS in the near future is what unlitatmely led me to try Unraid. So I took advantage of their 30-day free trial, loaded the OS onto a flash drive, and quickly fell in love with the simplicity and level of customizability that the Unraid UI offers.

Unraid is an all-in-one solution to creating a well-rounded home server. It allows me to easily add storage with many forms of redunancy to choose from, setup user shares, create virtual machines, run docker containers and more. Some services/applications that I am currently running are Heimdall, Nginx Proxy Manager, Authelia, and Home Assistant. Click one of these buttons to read more about these services and why I am using them.

[Heimdall]({{ site.baseurl }}{% link docs/homelab/heimdall}){: .btn } [Nginx]({{ site.baseurl }}{% link docs/homelab/nginx}){: .btn } [Authelia]({{ site.baseurl }}{% link docs/homelab/authelia}){: .btn } [Home Assistant]({{ site.baseurl }}{% link docs/homelab/homeassistant}){: .btn }

---

