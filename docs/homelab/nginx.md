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

### How it works

When you try to access a specified subdomain within your network, for example heimdall.yourdomain.org, your browser will:
  1. Contact the nameservers used by your domain (Cloudflare)
  2. Cloudflare DNS will redirect you to your local Nginx Proxy Manager
  3. Nginx Proxy Manager will see the source address (heimdall.yourdomain.org) and check the configured proxy hosts
  4. If an valid proxy host is configured, Nginx Proxy Manager will redirect you to the destination ip address and port with an HTTPS connect if enabled 

## Configuration

### Requirements

A few things you will need for this configuration:
  - Registered domain name
  - Free Cloudflare account
  - Nginx Proxy Manager

### Step 1: Setup your domain to use Cloudflare nameservers
1. View your assigned nameservers inside the `DNS` tab of Cloudflare.
  <img src="/assets/images/nginx_cloudflarenameservers.png" alt="Cloudflare Nameservers">
2. Set your custom nameservers within your domain provider as the nameservers assigned in Cloudflare. For example, within Google Domains:
  <img src="/assets/images/nginx_googlenameservers.png" alt="Google Domain Nameservers">

### Step 2: Create A and CNAME records within Cloudflare DNS
1. Create an **A record** that will direct traffic to your local Nginx Proxy Manager. The `Name` should consist of your root domain (yourdomain.org), and the `Content` should consist of the local IP address that is hosting Nginx Proxy Manager. For example:
  <img src="/assets/images/nginx_arecords.png" alt="Cloudflare A Records">
2. Then, create a **CNAME record** for each service you want to create a subdomain for. The `Name` should consist of the service name and the `Content` should consist of your root domain. For example:
  <img src="/assets/images/nginx_cnamerecords.png" alt="Cloudflare CNAME Records">

### Step 3: Create a wildcard SSL certificate using Let's Encrypt
1. Inside of Nginx Proxy Manager, go to the SSL Certificates tab
2. Click on `Add SSL Certificate`, then select `Let's Encrypt`
3. Under Domain Names, enter in your root domain with a wildcard (*) as the subdomain:
  ```
  EXAMPLE: *.yourdomain.org
  ```
4. Enter your email address and enable `Use a DNS Challenge`
5. `Save` your certificate

### Step 4: Create a Proxy Host within Nginx Proxy Manager

{: .note }
Some services, such as Heimdall, may require custom configuration that can be entered in the `Advanced` tab.

1. Create a **Proxy Host** that will direct the subdomain to the appropriate service. For example, this is the specific configuration for Heimdall:
  - `Domain Names` - heimdall.yourservice.org
  - `Scheme` - https
  - `Forward IP` - ip address of your heimdall
  - `Forward Port` - port of your heimdall
  - Enable `Websockets Support`
  - Select your Let's Encrypt `SSL Certificate`
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
2. Test your new subdomain to see if it redirects you to the correct ip address and port number. 

  {: .warning }
  If you receive an error, such as a 500 Internal Server Error, the problem may be:

  - Some services don't work well with HTTPS, try disabling SSL Certificates
  - If you haven't already, enable Websockets Support