---
title: "Network Enumeration"
date: 2022-08-24T14:30:58-05:00
draft: false
category: Networking
tags:
- Network
- Tools
---

## NMAP
{{< highlight bash >}}
# Host Discovery - no port scan
nmap -sn 192.168.1.0/24
# Port Discovery - using list of IPs
nmap -iL <ip list>
# Service delatils
nmap -iL <ip list> -sV
# Details and OS ID
nmap -iL <ip list> -sV -O

# T4 for faster execution
nmap -sV --allports -T4 192.168.1.0/24
{{< / highlight >}}

## Network Tools
nmap, ping, traceroute, netstat, ns lookup, and dig

