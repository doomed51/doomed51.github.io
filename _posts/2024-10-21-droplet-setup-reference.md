---
layout: post
title: "Digitalocean droplet setup"
tags: [references]
author: Rachit 
---

> Getting started
- [Initial Ubuntu setup](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-20-04)
- [Setting up SSH Keys](https://docs.digitalocean.com/products/droplets/how-to/add-ssh-keys/)
- [Disabling password authentication](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-20-04#step-4-disabling-password-authentication-on-your-server)
- [Installing Fail2Ban](https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-fail2ban-on-ubuntu-20-04)

> Firewall
- `ufw status`
- `ufw app list`: available applications 
- `ufw allow/block <application>`: edit rules  
- `ufw <enable/disable>`

> General
- On load always `sudo apt update && sudo apt upgrade`