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

## Configuration

### Requirements

A few things you will need for this configuration:
- Public domain name
- Cloudflare account
- Nginx Proxy Manager

### Step 1: Set your domain to use Cloudflare nameservers
1. View your assigned Cloudflare nameservers inside the `DNS` tab of your domain.
  <img src="/assets/images/nginx_cloudflarenameservers.png" alt="Cloudflare Nameservers">
2. Set your custom nameservers within your domain provider. For example, within Google Domains:
  <img src="/assets/images/nginx_googlenameservers.png" alt="Google Domain Nameservers">

### Step 2: Setup A and CNAME records within Cloudflare DNS
1. Create an **A record** that will direct traffic to your local Nginx Proxy Manager. The `Name` should consist of your domain name and top-level domain, and the `Content` should consist of the local IP address that is hosting Nginx Proxy Manager. For example:
  <img src="/assets/images/nginx_arecords.png" alt="Cloudflare A Records">
2. Then, create a **CNAME record** for each service you want to create a subdomain for. The `Name` should consist of the service name and the `Content` should consist of your domain name and top-level domain. For example:
  <img src="/assets/images/nginx_cnamerecords.png" alt="Cloudflare CNAME Records">