---
title: "Fresh Ubuntu Install"
date: 2021-12-13T00:43:09-06:00
draft: false
category: Snippits
tags:
- Ubuntu
---



## Add new user:
sudo adduser [username]
-> promtped for password and info

## Add user to sudo group:
sudo usermod -aG sudo [username]

## Remove user and home directory:
sudo deluser --remove-home [username]

## Install ZeroTier:
curl -s https://install.zerotier.com | sudo bash
sudo zerotier-cli join [network_id] # Then approve on website
### get new ZT address
sudo systemctl stop zerotier-one
sudo rm /var/lib/zerotier-one/identity.public /var/lib/zerotier-one/identity.secret
sudo systemctl start zerotier-one

## Install docker
sudo usermod -aG docker [username]

## Set up git
git config --global user.name "Your Name"
git config --global user.email "youremail@yourdomain.com"
git config --global credential.helper store

## Oracle open ports
sudo iptables -I INPUT -j ACCEPT  # if works, do following
sudo su
iptables-save > /etc/iptables/rules.v4
exit