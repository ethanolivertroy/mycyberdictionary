# Simple Mail Transfer Protocol (SMTP)

## Overview
- Internet standard communication protocol for sending email messages between email servers
- Operates over TCP/IP networks
- Default port: 25
  - Port 587: Mail submission (STARTTLS)
  - Port 465: SMTP over SSL/TLS (deprecated, but still in use)

## Key Components
- SMTP commands: HELO, EHLO, MAIL, RCPT, DATA, QUIT, etc.
- SMTP responses: 3-digit status codes (2xx, 4xx, 5xx)

## Common Security Issues
- Open relays
- User enumeration (VRFY, EXPN)
- Insecure configurations (lack of encryption, weak authentication)
- Vulnerable software versions

--------


To identify systems that respond to SMTP and check the reply code for the root user using the VRFY command, follow these steps:

1. Power on the Walk Through Exercises VM Group 1.

2. Open a terminal on your Linux machine.

3. Use Nmap to scan for open SMTP ports (usually port 25) in the target IP range:

```bash
nmap -p 25 <target_IP_range>
```

Replace `<target_IP_range>` with the actual IP range or list of IP addresses you want to scan in the VM Group 1.

4. Review the Nmap output and take note of the IP addresses with open SMTP ports.

5. For each machine with an open SMTP port, open a connection to port 25 using Netcat:

```bash
nc <IP_address> 25
```

Replace `<IP_address>` with the IP address of each machine identified in the previous step.

6. Once connected, run the VRFY command against the root user:

```
VRFY root
```

7. Check the reply code sent by the SMTP server as a response to the VRFY command. It will be a three-digit number at the beginning of the response line.

Please ensure you have permission to perform the port scanning and interact with the target IP range, as unauthorized scanning and actions may be illegal or against network policies.