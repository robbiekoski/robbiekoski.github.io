---
layout: default
title: Home Assistant
parent: Homelab
nav_order: 6
---

# Home Assistant
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Details

One of the main reasons for creating my homelab in the first place was because of my interest in home automation. I first got the idea of creating a smart home a few years ago when my friend explained to me what [Home Assistant](https://www.home-assistant.io/) was and how he incorporated it into his daily life. From customizing your own dashboard, to creating convenient automations, and even integrating different wireless device protocols enabling them to communicate together. These are just some of the features that Home Assistant provides in its open-source project to give control back to the average smart home consumer. 

The biggest problem with smart home products nowadays is the fact that most brands have their own ecosystems that only allow their products to be configured using their proprietary app. Did you buy a new smart lightbulb for your house? Well, chances are if you already have multiple brands of smart bulbs then you're going to be adding another app to your smartphone in order to pair and use it. Yes, you could use something like Apple Homekit for homekit-compatible devices, however, this doesn't solve the problem that many of these devices also require a brand-specific hub in order to pair them in the first place. This is where Home Assistant can help with its community-driven integrations feature that allows you to pair many different brands of devices straight to the application itself. 

---

## Integrations and Add-ons

As mentioned above, [integrations](https://www.home-assistant.io/integrations/) within Home Assistant are created and updated by the community. This allows for device brands such as Ikea TRADFRI, Phillips Hue, Sonoff and many more to be natively paired with Home Assistant without the use of a hub. Simplifying the amount of hubs in your smart home network will help reduce the points of failure and headache when something inevitably goes wrong. The Add-on Store takes advantage of Home Assistant running as a virtual machine to provide users with the ability to install many optional services such as Samba file server, Node-RED, Let's Encrypt, and more. 

---

## My Dashboard

I am currently using a theme called [Mushroom](https://github.com/piitaya/lovelace-mushroom) that allows me to use custom cards on my dashboard. This theme is very easy to setup and is meant to be viewed on both desktops and smartphones.

---

## Screenshots

<div class="code-example">
<img src="/assets/images/homeassistant_mobile.png" alt="Home Assistant Mobile Dashboard"> 
</div>