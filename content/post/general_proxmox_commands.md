---
title: "General Proxmox Commands"
date: 2021-12-12T23:48:53-06:00
draft: false
category: Commands
tags:
- Proxmox
---

## Unlock locked VM
{{< highlight bash >}}
qm unlock <VM_NUMBER>
# or
pct unlock <LXC_NUMBER> # for CT
{{< / highlight >}}

## Descend into LXC from PVE
lxc-attach --name <LXC_NUMBER>