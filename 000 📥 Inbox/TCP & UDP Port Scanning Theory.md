OSCP (Offensive Security Certified Professional) is a certification focused on hands-on penetration testing. When preparing for the OSCP exam, understanding the theory behind TCP and UDP port scanning is essential. Here are some notes to help you understand the basics:

TCP/UDP Port Scanning Theory:

1. Ports and Protocols:
   - TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are two primary transport layer protocols.
   - TCP is connection-oriented, reliable, and ensures data is delivered correctly, while UDP is connectionless, faster, and doesn't guarantee data delivery.
   - Ports are used to identify specific services running on a machine. They range from 0 to 65535, with well-known ports being 0 to 1023.

2. Port Scanning Objectives:
   - Identify open, closed, or filtered ports on a target machine.
   - Discover services running on a target machine.
   - Enumerate version information for detected services.
   - Uncover potential vulnerabilities in services.

3. Common TCP Scanning Techniques:
   - SYN scan (half-open scan): Sends a SYN packet to the target port. If an open port responds with a SYN/ACK packet, the scanner sends a RST packet, preventing a full connection.
   - Connect scan: Establishes a full TCP connection to the target port, making it reliable but easily detectable.
   - ACK scan: Sends an ACK packet to the target port. Useful for determining firewall rules, but not for identifying open ports.
   - FIN, NULL, and Xmas scans: Stealthier scanning techniques that rely on specific flag combinations to elicit responses from target ports.

4. Common UDP Scanning Techniques:
   - UDP scan: Sends a UDP packet to the target port. If the port is closed, it responds with an ICMP "Port Unreachable" message. Open ports may not respond, making UDP scanning less reliable.
   - Version scanning: Sends a probe specific to a known service to the target port, attempting to elicit a response revealing service information.

5. Tools for Port Scanning:
   - Nmap: The most popular and versatile port scanning tool, supporting various scanning techniques and additional features like OS fingerprinting and scripting.
   - Netcat: A simple and flexible tool that can be used for port scanning, transferring files, and creating backdoors.
   - Masscan: A high-speed port scanner, useful for scanning large networks quickly but with limited scanning techniques.

6. Ethical Considerations:
   - Always have explicit permission to perform port scanning on a target machine or network.
   - Unauthorized scanning may be illegal or against network policies.
   - Be aware of the potential impact on network resources, and consider rate limiting or scheduling scans during off-peak hours.

These notes cover the essential aspects of TCP and UDP port scanning theory for the OSCP exam. It's important to practice using these scanning techniques and tools in a controlled and legal environment to develop your skills and understanding.

```
nc -nvv -w 3 -z 192.168.XXX.151 1-100
```

```
nc -nv -u -z -w 5 192.168.209.151 100-200

```
