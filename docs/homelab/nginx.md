---
layout: default
title: Nginx Proxy Manager
parent: Homelab
nav_order: 4
---

# Nginx Proxy Manager
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Details

I am currently using [Nginx Proxy Manager](https://nginxproxymanager.com/guide/), with the help of Cloudfare's free DNS services, to help redirect my public domain to my internal services on my network. By doing this, I can also utilize Let's Encrypt within Nginx to enable SSL encryption while accessing my services.

### Requirements



## Configuration

A few things you will need for this configuration:
- Public domain
- Cloudflare account
- Nginx Proxy Manager

### Requirements

### Set your domain to use Cloudflare nameservers
1. View your assigned Cloudflare nameservers inside the `DNS` tab of your domain.
  <img src="/assets/images/heimdall.png" alt="Cloudflare Nameservers"> 
2. Set your custom nameservers within your domain provider. For example, Google Domains:
  <img src="/assets/images/heimdall.png" alt="Google Domain Nameservers">
