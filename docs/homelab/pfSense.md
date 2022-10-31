---
layout: default
title: pfSense
parent: Homelab
---

# pfSense
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background
When I started planning for my home network I knew that I wanted to incorporate a dedicated, easily manageable, open source firewall. There were a couple of options that I was choosing from, however, my friend recommended that I check out [pfSense](https://www.pfsense.org/). So I did, and never looked back. Currently running on a fanless Mini PC from [Qotom](https://www.qotom.net/), my pfSense box serves as my router, firewall, DHCP server, and more that is all easily configurable within a convenient web-based dashboard.

---

## Network Layout
The Qotom Mini PC that I use to run pfSense has a total of 4 NIC ports that allows me to create 3 separate LAN interfaces (because 1 port is always used for `WAN` uplink). My network is segmented into two interfaces because I want to be able to control how home and guest devices communicate with my homelab services.

The first interface, simply called `LAB`, is reserved only for devices within my homelab including my main computer, Raspberry Pi projects, and Unraid server along with all of its services. The second interface is called `GUEST` and it is used for all other Wi-Fi and IoT devices around the house such as phones, tablets, laptops, smart TVs, etc. Only select devices from the `GUEST` interface, such as smart home devices, are allowed to communicate with the LAB interface in order to limit the amount of devices that can contact my Unraid server.

| Interface    | Use                     | Rules                                       |
|:-------------|:------------------------|:--------------------------------------------|
| WAN          | WAN Uplink to ISP modem | Can communicate with LAN & GUEST            |
| LAB          | Homelab devices         | Can communicate with WAN & GUEST            |
| GUEST        | Wi-Fi and IoT devices   | Can communicate with WAN & limitedly to LAN |