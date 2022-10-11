---
title: "Proxmox Expand HD Space"
date: 2021-12-12T23:40:44-06:00
draft: false
category: Snippits
tags:
- Proxmox
---

## Expand HD space in Proxmox VM
{{< highlight bash >}}
lsblk
sudo fdisk -l /dev/sda
sudo parted /dev/sda
  - print
  - F (fix)
  - resizepart 3 100%
  - quit
sudo fdisk -l /dev/sda
sudo pvresize /dev/sda3
sudo lvextend ubuntu-vg/ubuntu-lv -l+100%FREE
sudo resize2fs /dev/ubuntu-vg/ubuntu-lv
sudo reboot
{{< / highlight >}}
