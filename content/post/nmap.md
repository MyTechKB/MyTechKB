---
title: "Nmap Information"
date: 2022-06-30T14:30:58-05:00
draft: false
category: Networking
tags:
- Network
- Tools
---

## Options
NMAP:
- Live Host Discovery:
  - ARP Scan                sudo nmap -PR -sn MACHINE_IP/24
  - ICMP Echo Scan          sudo nmap -PE -sn MACHINE_IP/24
  - ICMP Timestamp Scan     sudo nmap -PP -sn MACHINE_IP/24
  - ICMP Address Mask Scan  sudo nmap -PM -sn MACHINE_IP/24
  - TCP SYN Ping Scan       sudo nmap -PS22,80,443 -sn MACHINE_IP/30
  - TCP ACK Ping Scan       sudo nmap -PA22,80,443 -sn MACHINE_IP/30
  - UDP Ping Scan           sudo nmap -PU53,161,162 -sn MACHINE_IP/30
  - OPTION -n:                     Do not send DNS queries
  - OPTION -sn:                    Host discovery without port-scanning
- Basic Port Scans:
  - TCP Connect Scan        nmap -sT MACHINE_IP
  - TCP SYN Scan            sudo nmap -sS MACHINE_IP
  - UDP Scan                sudo nmap -sU MACHINE_IP
  - OPTION -p-:                    all ports
  - OPTION -p1-1023:               scan ports 1 to 1023
  - OPTION -F:                     100 most common ports (default 1000)
  - OPTION -r:                     scan ports in consecutive order
  - OPTION -T<0-5>:                -T0 being the slowest and T5 the fastest
                                     T4 used in CTF, T1 in real engagements
  - OPTION --max-rate 50:          rate <= 50 packets/sec
  - OPTION --min-rate 15:          rate >= 15 packets/sec
  - OPTION --min-parallelism 100:  at least 100 probes in parallel
- Advanced Port Scans:
  - TCP Null Scan        sudo nmap -sN MACHINE_IP
  - TCP FIN Scan         sudo nmap -sF MACHINE_IP
  - TCP Xmas Scan        sudo nmap -sX MACHINE_IP
  - TCP Maimon Scan      sudo nmap -sM MACHINE_IP (only works on BSD)
  - TCP ACK Scan         sudo nmap -sA MACHINE_IP (tests firewall rules)
  - TCP Window Scan      sudo nmap -sW MACHINE_IP (tests firewall rules)
  - Custom TCP Scan      sudo nmap --scanflags URGACKPSHRSTSYNFIN MACHINE_IP
  - Spoofed Source IP    sudo nmap -S SPOOFED_IP MACHINE_IP
  - Decoy Scan           nmap -D DECOY_IP,ME MACHINE_IP
  - Idle (Zombie) Scan   sudo nmap -sI ZOMBIE_IP MACHINE_IP
  - OPTION --spoof-mac SPOOFED_MAC:  Spoofed MAC Address
  - OPTION -f:                       Fragment IP data into 8 bytes
  - OPTION -ff:                      Fragment IP data into 16 bytes
  - OPTION --source-port PORT_NUM:   specify source port number
  - OPTION --data-length NUM:        append random data to reach given length
  - OPTION --reason:                 explains how Nmap made its conclusion
  - OPTION -v:                       verbose
  - OPTION -vv:                      very verbose
  - OPTION -d:                       debugging
  - OPTION -dd:                      more details for debugging
- Post Port Scans:
  - OPTION -sV:                      determine service/version info on open ports
  - OPTION -sV --version-light:      try the most likely probes (2)
  - OPTION -sV --version-all:        try all available probes (9)
  - OPTION -O:                       detect OS
  - OPTION --traceroute:             run traceroute to target
  - OPTION --script=SCRIPTS:         Nmap scripts to run
  - OPTION -sC or --script=default:  run default scripts
  - OPTION -A:                       equivalent to -sV -O -sC --traceroute
  - OPTION -oN:                      save output in normal format
  - OPTION -oG:                      save output in grepable format
  - OPTION -oX:                      save output in XML format
  - OPTION -oA:                      save output in normal, XML and Grepable formats

Script Category | Description
- auth -              Authentication related scripts
- broadcast -         Discover hosts by sending broadcast messages
- brute -             Performs brute-force password auditing against logins
- default -           Default scripts, same as -sC
- discovery -         Retrieve accessible information, such as database tables and DNS names
- dos -               Detects servers vulnerable to Denial of Service (DoS)
- exploit -           Attempts to exploit various vulnerable services
- external -          Checks using a third-party service, such as Geoplugin and Virustotal
- fuzzer -            Launch fuzzing attacks
- intrusive -         Intrusive scripts such as brute-force attacks and exploitation
- malware -           Scans for backdoors
- safe -              Safe scripts that won’t crash the target
- version -           Retrieve service versions
- vuln -              Checks for vulnerabilities or exploit vulnerable services

