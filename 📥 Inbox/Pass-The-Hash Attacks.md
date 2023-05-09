---
description: 
cover: 
---
Last Updated 2023-05-08

#red-team 
# Pass-The-Hash Attacks

<iframe width="560" height="315" src="https://www.youtube.com/embed/EsyUa63NM1E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## What is a pass-the-hash attack?

- Pass-the-hash (PtH) attacks occur when a malicious actor steals a hashed user credential and uses it to create a new user session on the same network.
- Unlike other credential theft attacks, PtH attacks don't require the attacker to know or crack the password to gain access to the system. Instead, they use the stored version of the password to initiate a new session.

## What is a password hash?

A password hash is a one-way mathematical function that converts a user's password into a text string that cannot be reversed or decoded to reveal the actual password. Passwords are stored as hash symbols, not as text or characters.

## Why are pass-the-hash attacks a growing concern?

With more organizations leveraging single sign-on (SSO) technology to enable remote workforces and reduce friction in user experiences, attackers have recognized the inherent vulnerability of stored passwords and user credentials. 
Identity-based attacks, such as PtH attacks, are difficult to detect because most traditional cybersecurity solutions cannot differentiate between a real user and an attacker masquerading as one. 
These attacks can lead to more severe security issues like data breaches, identity theft, and malware or ransomware attacks.

## How does a pass-the-hash attack work?

In a PtH attack, the attacker typically gains access to the network through a social engineering technique, such as phishing. Once the attacker gains access to the user's account, they use tools and techniques to scrape active memory for data leading to hashes. With one or more valid password hashes, the attacker gains full system access, enabling lateral movement across the network, hash harvesting, adding account privileges, targeting privileged accounts, and setting up backdoors for future access.

## Who is vulnerable to pass-the-hash attacks?

Windows server clients and organizations using Windows New Technology LAN Manager (NTLM) are particularly vulnerable to PtH attacks. NTLM is a suite of Microsoft security protocols that authenticate users' identity and protect the integrity and confidentiality of their activity. It is an SSO tool that relies on a challenge-response protocol to confirm the user without requiring them to submit a password, a process known as NTLM authentication.

## How to mitigate pass-the-hash attacks?
....

## Links:
- https://www.crowdstrike.com/cybersecurity-101/pass-the-hash/