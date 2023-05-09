# NMAP

Nmap stands for "Network Mapper." It is a widely-used open-source tool for network discovery and security auditing. Nmap helps in host discovery, port scanning, service and version detection, operating system fingerprinting, and running various security checks using its scripting engine (NSE).

https://nmap.org/book/

## Interesting

- https://nmap.org/book/man-bypass-firewalls-ids.html

## NMAP Cheat Sheet

| Section                 | Command / Description                     |
|-------------------------|-------------------------------------------|
| **Overview**            |                                           |
|                         | Nmap is a versatile open-source tool for network discovery and security auditing |
| **Basic Scanning Techniques** |                                     |
| Ping sweep              | `nmap -sn TARGETS`                        |
| Basic port scan         | `nmap -p- TARGETS`                        |
| Service/version detection | `nmap -sV TARGETS`                      |
| OS fingerprinting       | `nmap -O TARGETS`                         |
| Aggressive scan         | `nmap -A TARGETS`                         |
| **Scan Types**          |                                           |
| SYN scan (default)      | `nmap -sS TARGETS`                        |
| Connect scan            | `nmap -sT TARGETS`                        |
| UDP scan                | `nmap -sU TARGETS`                        |
| ACK scan                | `nmap -sA TARGETS`                        |
| SCTP scan               | `nmap -sY TARGETS`                        |
| **Timing and Performance** |                                       |
| Timing templates (0-5)  | `nmap -T4 TARGETS`                        |
| Customize timing options | `nmap --min-rate 1000 --max-retries 2 TARGETS` |
| **Output Formats**      |                                           |
| Normal output           | `nmap -oN output.txt TARGETS`             |
| XML output              | `nmap -oX output.xml TARGETS`             |
| Grepable output         | `nmap -oG output.gnmap TARGETS`           |
| All formats             | `nmap -oA output TARGETS`                 |
| **Nmap Scripting Engine (NSE)** |                                  |
| Run default scripts     | `nmap --script=default TARGETS`           |
| Run specific scripts    | `nmap --script=script1,script2 TARGETS`   |
| Run scripts by category | `nmap --script=category TARGETS`          |
