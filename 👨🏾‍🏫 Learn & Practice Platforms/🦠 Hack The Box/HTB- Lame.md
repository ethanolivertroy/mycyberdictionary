---
date: 2023-03-12
lastmod: 2023-03-12
tags: ["SAMBA"]
categories: ["Hack The Box", "TJ Null's OSCP List"]
description: "One of the first HTB boxes I solved a few months ago from the TJ Null List in preparation for the PNPT and OSCP."
---

# Hack the Box — Lame

Just another TJ Null box preparing for the OSCP on a Sunday.

![](https://cdn-images-1.medium.com/max/1600/1*EvZ67a9vFkG-bLwf9FNJZg.png)

## Recon

`nmap -sC -sV -O -oA nmap/initial 10.10.10.3`

![](https://cdn-images-1.medium.com/max/1600/1*wyUit7q0MSiYl6RnYtJSmw.png)

`nmap -sC -sV -O -p- -oA nmap/full 10.10.10.3`

![](https://cdn-images-1.medium.com/max/1600/1*FCzc3HlPu4FxBtseqYPGiw.png)

`nmap -sU -O -p- -oA nmap/udp 10.10.10.3`

![](https://cdn-images-1.medium.com/max/1600/1*bfZghvXUTlxbC0Ewbz-SeQ.png)

## Enumeration

I use `searchsploit` to check for exploits for these open ports and services.

I have a feeling it will be something SAMBA related that will work.

Let’s look into that Port 21 vsftpd v2.3.4:

![](https://cdn-images-1.medium.com/max/1600/1*6qav25nSAgr1OJl0BPEEdg.png)

Looks like the first 3 google results show there is a backdoor command execution

Use an NMAP script to see if this will work on this machine

![](https://cdn-images-1.medium.com/max/1600/1*XvGf287mQkTdRGgb1ESXFQ.png)

nmap --script ftp-vsftpd-backdoor -p 21 10.10.10.3

![](https://cdn-images-1.medium.com/max/1600/1*JI2JXyFOKyvvz62tVF1srw.png)

Looks like this won’t work

Let's try that SAMBA thing I was having feelings about 😂

I check `searchsploit` for samba 3.0.20 and find an exploit BUT its for Metasploit and I want to do this manually for the OSCP so…

![](https://cdn-images-1.medium.com/max/1600/1*HakeG8i6FKbdU-PJzpQDOw.png)

We check the actual exploit-db page and find the CVE and maybe I can find a GitHub hosted exploit that I can just configure and run?

![](https://cdn-images-1.medium.com/max/1600/1*Ae7dbj-9UKFyIr9ohmpENg.png)

## Exploitation

Using [https://github.com/amriunix/CVE-2007-2447](https://github.com/amriunix/CVE-2007-2447)

![](https://cdn-images-1.medium.com/max/1600/1*HiTP3R8tUMKdLoT-hnBYcA.png)

Upgrade the shell with:

python -c ‘import pty; pty.spawn(“/bin/sh”)’

![](https://cdn-images-1.medium.com/max/1600/1*tF7Qu7dIIZKsNmz4ADlhtQ.png)

## Thoughts

-   SAMBA stuff always seems to be vulnerable in this old retired boxes, so when I see it I will go down that path over something else like ssh
-   After doing a few of these boxes you realize this formulaic process of recon, enumeration, and exploitation.
-   The tricky part between enumeration and exploitation is finding dead ends fast, using experience to realize where the real attack point should be, and adjusting exploits in order to gain the position in the machine I’m looking for
-   From a security perspective, a lot of these vulnerabilities are only possible to exploit because they are running and not being patched
-   In order to protect from these attacks systems need to know what they have running in their environment and constantly be aware of if they are behind or up-to-date on patches.
-   Tools like Tenable Nessus can be useful for discovering and working on these remediations but sometimes some manual work needs to be put in if the vulnerability is relatively new