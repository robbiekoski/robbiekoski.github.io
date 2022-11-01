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

I am currently using [Nginx Proxy Manager](https://nginxproxymanager.com/guide/), with the help of Cloudfare's free DNS services, to help redirect my public domain name to my internal services on my network. By doing this, I can also utilize Let's Encrypt within Nginx to enable SSL encryption while accessing my services. Because my network is not exposed to the internet, this was more of a convenience project for me because now I don't have to remember the ip address and port numbers for each service. Also having SSL certificates on your local services is kinda cool.

As mentioned above, this setup only works when connected to my local network because my domain name redirects to a private ip address (my nginx proxy manager). Anyone who tries to access my domain outside of my network will receive a time out error because they will be connecting to an ip address that doesn't exist on their network. 

## Configuration

### Requirements

A few things you will need for this configuration:
- Registered domain name
- Cloudflare account
- Nginx Proxy Manager

### Step 1: Setup your domain to use Cloudflare nameservers
1. View your assigned nameservers inside the `DNS` tab of Cloudflare.
  <img src="/assets/images/nginx_cloudflarenameservers.png" alt="Cloudflare Nameservers">
2. Set your custom nameservers within your domain provider as the nameservers assigned in Cloudflare. For example, within Google Domains:
  <img src="/assets/images/nginx_googlenameservers.png" alt="Google Domain Nameservers">

### Step 2: Create A and CNAME records within Cloudflare DNS
1. Create an **A record** that will direct traffic to your local Nginx Proxy Manager. The `Name` should consist of your domain name and top-level domain, and the `Content` should consist of the local IP address that is hosting Nginx Proxy Manager. For example:
  <img src="/assets/images/nginx_arecords.png" alt="Cloudflare A Records">
2. Then, create a **CNAME record** for each service you want to create a subdomain for. The `Name` should consist of the service name and the `Content` should consist of your domain name and top-level domain. For example:
  <img src="/assets/images/nginx_cnamerecords.png" alt="Cloudflare CNAME Records">

### Step 3: Create a wildcard SSL certificate using Let's Encrypt
1. Inside of Nginx Proxy Manager, go to the SSL Certificates tab
2. Click on `Add SSL Certificate`, then select `Let's Encrypt`
3. Under Domain Names, enter in your domain name with a wildcard (*) as the subdomain:
  ```
  EXAMPLE: *.yourdomain.org
  ```
4. Enter your email address and enable `Use a DNS Challenge`
5. `Save` your certificate

### Step 4: Create a Proxy Host within Nginx Proxy Manager
1. Create a **Proxy Host** that will direct the subdomain to the appropriate service, enable SSL   For example:
{: .warning }
Some services, such as Heimdall, may require custom nginx configuration.
  - `Domain Names` - the full domain name including subdomain for the server (created in step 3b)
  - `Scheme` - https
  - `Forward IP` - the ip address of your heimdall
  - `Forward Port` - the port of your heimdall
  - Select your `SSL Certificate` using Let's Encrypt
  - Enable `Force SSL`
  - Enable `HTTP/2 Support`
  - Under `Advanced`, enter this into the Custom Nginx Configuration:
    ```
    location / {
    proxy_set_header Host $host;
    proxy_set_header X-Forwarded-Scheme $scheme;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Forwarded-For $remote_addr;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_pass $forward_scheme://$server:$port$request_uri;
    }
    ```