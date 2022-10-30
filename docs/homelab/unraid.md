---
layout: default
title: Unraid
parent: Homelab
---

# Unraid
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background
Before I eventually decided to use [Unraid](https://unraid.net/), I was running Proxmox to create and manage my virtual machines and containers. It was very helpful in initially learning the basics of virtualization, however, I felt myself wanting more. In addition, knowing that I wanted to build myself a NAS in the near future is what unlitatmely led me to try Unraid. So I took advantage of their 30-day free trial, loaded the OS onto a flash drive, and quickly fell in love with the simplicity and level of customizability that the Unraid UI offers.

Unraid is an all-in-one solution to creating a well-rounded home server. It allows me to easily add storage with many forms of redunancy to choose from, setup user shares, create virtual machines, run docker containers and more. Some services/applications that I am currently running are Heimdall, Nginx Proxy Manager, Authelia, and Home Assistant.

---

## Array Setup
Inside of my array setup I currently have `1 4TB data disk`, `1 4TB parity disk`, and `1 500GB SSD cache disk`. With this setup (1 data drive and 1 parity drive), I have 4TB of usable space with the ability to recover all data in the event of 1 drive failure. The cache drive is extremely useful in providing fast initial read/write speeds when copying data to shares. Data is first copied onto the cache disk drive utilizing its fast performance and then moved to the parity-protected data disks with the help of a mover utility that runs overnight. In the future I plan on adding one more data drive, however, for now this is plenty of space for my media shares.


| Type        | Identification             | Size    |
|:------------|:---------------------------|:--------|
| Disk 1      | Seagate NAS ST4000VN008    | 4TB     |
| Parity      | Seagate NAS ST4000VN008    | 4TB     |
| Cache       | Crucial P2 CT500P2SSD8     | 500GB   |

---

## Screenshots

<img src="/assets/images/unraid_dashboard.png" alt="Unraid Dashboard Page"> <img src="/assets/images/unraid_main_edited.png" alt="Unraid Main Page"> 

---