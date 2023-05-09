# Information Gathering

- Attack surfaces shift as a result of emerging software flaws, configuration blunders, or IT restructuring that unveils new areas for exploitation.

## Important
- Thoroughly mapping an attack surface using both passive and active methods
- Utilizing the collected data during the entire penetration test process

# Passive Information Gathering

## Whois Enumeration
- Use the `whois` command to gather information about a domain or an IP address:
```
whois example.com
whois 192.0.2.1
```
## Google Hacking
- Use Google dorks to find specific information or files in websites:
```
site:example.com filetype:pdf
intitle:"index of" inurl:ftp
```

## Netcraft
- Use the Netcraft Site Report to gather information about a domain or an IP address (not available via command line, but access through a web browser):
	- ```https://sitereport.netcraft.com/?host=example.com```
	- https://searchdns.netcraft.com/

## Open-Source Code
-   Use GitHub search to find sensitive information in repositories:
```
https://github.com/search?q=user%3Ausername+password&type=Code
```

## Shodan
-   Use the Shodan command-line interface (CLI) to search for devices or services. First, install the Shodan CLI:
```
pip install shodan
```
-   Initialize the CLI with your API key:
```
shodan init YOUR_API_KEY
```
-   Perform a search:
```
shodan search "Apache/2.4.7"
```
``

## Security Headers and SSL/TLS
- Use `curl` to check HTTP security headers:
```
curl -sI https://example.com | grep -E 'Strict-Transport-Security|Content-Security-Policy|X-Content-Type-Options|X-Frame-Options|X-XSS-Protection'
```
- Use `openssl` to check SSL/TLS certificate information:
```
echo | openssl s_client -connect example.com:443 | openssl x509 -noout -text
```
- https://securityheaders.com/

# Active Information Gathering

## DNS Enumeration

>With mx, the lower the priority value, the higher the priority of the mail server.

- nslookup: `nslookup example.com`
- dig: `dig example.com`
- host: `host 192.0.2.1`
- dnsrecon: `dnsrecon -d example.com`
- subfinder: `subfinder -d example.com`

```bash
nslookup -type=TXT info.exmple.com 192.168.209.151
```

```bash
dnsenum --enum -f /usr/share/dnsenum/dns.txt example.com
```

## Port Scanning with [[NMAP]]
- Basic scan: `nmap -sV -p- example.com`
- Scan with OS fingerprinting and default scripts: `nmap -A -p- example.com`

## SMB Enumeration
- smbclient: `smbclient -L \\\\TARGET_IP\\ -U ""`
- enum4linux: `enum4linux -a TARGET_IP`
- nmap scripts: `nmap -p 445 --script smb-vuln-* TARGET_IP`

```
C:\Users\student>net view \\dc01 /all
Shared resources at \\dc01

Share name  Type  Used as  Comment

-------------------------------------------------------------------------------
ADMIN$      Disk           Remote Admin
C$          Disk           Default share
IPC$        IPC            Remote IPC
NETLOGON    Disk           Logon server share
SYSVOL      Disk           Logon server share
The command completed successfully.
```

## SMTP Enumeration
- smtp-user-enum: `smtp-user-enum -M VRFY -U users.txt -t TARGET_IP`
- nmap scripts: `nmap -p 25 --script smtp-vuln-* TARGET_IP`

## SNMP Enumeration
- snmpwalk: `snmpwalk -v 2c -c public TARGET_IP`
- snmp-check: `snmp-check TARGET_IP`
- nmap scripts: `nmap -p 161 --script snmp-* --script-args snmpcommunity=public TARGET_IP`