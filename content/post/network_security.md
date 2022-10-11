---
title: "Network and Security"
date: 2022-06-30T14:51:32-05:00
draft: false
category: Networking
tags:
- Network
- Security
- Tools
---

- OSI Model:
  - Application (7) - HTTP, FTP, SMTP, POP3, IMAP, etc.
  - Presentation (6) - SSL/TLS
  - Session (5)
  - Transport (4) - TCP, UDP
  - Network (3) - IPv4, IPv6
  - Data Linkn (2)
  - Physical (1) - network cards, cables

- TCP/IP Model: (older)
  - Application (7,6,5)
  - Transport (4)
  - Internet (3)
  - Network Interface (2,1)


- Confidentiality, Integrity, and Availability (CIA):
  - Confidentiality refers to keeping the contents of the communications accessible to the intended parties. 
  - Integrity is the idea of assuring any data sent is accurate, consistent, and complete when reaching its destination.
  - Availability refers to being able to access the service when we need it. 

  - Different parties will put varying emphasis on these three. For instance, confidentiality would be the highest priority for an intelligence agency. Online banking will put most emphasis on the integrity of transactions. Availability is of the highest importance for any platform making money by serving ads.

  - Knowing that we are protecting the Confidentiality, Integrity, and Availability (CIA), an attack aims to cause Disclosure, Alternation, and Destruction (DAD)




Protocol     TCP Port     Application(s)     Data Security     TLS Port
FTP          21           File Transfer      Cleartext         990
HTTP         80           Worldwide Web      Cleartext         443
IMAP         143          Email (MDA)        Cleartext         993
POP3         110          Email (MDA)        Cleartext         995
SMTP         25           Email (MTA)        Cleartext         465
Telnet       23           Remote Access      Cleartext


Pentesting: red team (attackers), blue team (defenders)
- nmap
- wireshark, tcpdump, tshark (sniffing attacks)
- metasploit - msfconsole
- ettercap, bettercap (man in the middle attacks)
- burp suite - webapp pentesting
- Password:
  - hydra -l username -P wordlist.txt server service
  - john the ripper - john


Network Security:
- Passive Recon - publicly available knowledge
  - whois DOMAINNAME - whois records
  - nslookup -type=??? DOMAINNAME DNSserver - dns records
  - dig @DNSserver DOMAINNAME TYPE - dns records
  - DNSDumpster.com - shows subdomains
  - Shodan.io

- Active Recon - requires direct engagement with the target
  - browser extensions
    - User-Agent Switcher and Manager
    - Wappalyzer
