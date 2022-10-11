---
title: "Remove Snap from Ubuntu"
date: 2021-12-12T23:45:45-06:00
draft: false
category: Snippits
tags:
- Ubuntu
---

## Remove snap from ubuntu
{{< highlight bash >}}
snap list
sudo snap remove <package_name>  #(remove snapd last)
sudo umount /snap/core/xxxx
sudo umount /var/snap
sudo apt purge snapd
sudo apt autoremove
{{< / highlight >}}
