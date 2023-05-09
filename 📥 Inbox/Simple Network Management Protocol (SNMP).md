# Simple Network Management Protocol (SNMP)

## Overview
- Application-layer protocol for managing and monitoring network devices
- Operates over UDP
- Primary ports: 161 (queries), 162 (traps)

## Key Components
- SNMP agents: software running on network devices, providing information and responding to queries
- Network Management System (NMS): software that collects and processes information from SNMP agents
- Management Information Base (MIB): hierarchical database containing information about managed objects
- Object Identifiers (OIDs): unique identifiers for managed objects in the MIB

## Versions
- SNMPv1: original version with basic security features (community strings)
- SNMPv2c: improved performance, security still based on community strings
- SNMPv3: enhanced security with authentication and encryption

## Common Security Issues
- Weak or default community strings
- Unauthorized access to sensitive information
- Lack of authentication and encryption in SNMPv1 and SNMPv2c
- Misconfigurations


-----------

Over the years, we have often found that the Simple Network Management Protocol (SNMP) is not well-understood by many network administrators. This often results in SNMP misconfigurations, which can result in significant information leaks.

SNMP is based on UDP, a simple, stateless protocol, and is therefore susceptible to IP spoofing and replay attacks. Additionally, the commonly used SNMP protocols 1, 2, and 2c offer no traffic encryption, meaning that SNMP information and credentials can be easily intercepted over a local network. Traditional SNMP protocols also have weak authentication schemes and are commonly left configured with default public and private community strings.

Until recently, SNMPv3, which provides authentication and encryption, has been shipped to support only DES-56, proven to be a weak encryption scheme that can be easily brute-forced. A more recent SNMPv3 implementation supports the AES-256 encryption scheme.

Because all of the above applies to a protocol that is, by definition, meant to "Manage the Network," SNMP is another one of our favorite enumeration protocols.

Several years ago, OffSec performed an internal penetration test on a company that provided network integration services to a large number of corporate clients, banks, and other similar organizations. After several hours of scoping out the system, we discovered a large class B network with thousands of attached Cisco routers. It was explained to us that each of these routers was a gateway to one of their clients, used for management and configuration purposes.

A quick scan for default cisco / cisco telnet credentials discovered a single low-end Cisco ADSL router. Digging a bit further revealed a set of complex SNMP public and private community strings in the router configuration file. As it turned out, these same public and private community strings were used on every single networking device, for the whole class B range, and beyond – simple management, right?

An interesting thing about enterprise routing hardware is that these devices often support configuration file read and write through private SNMP community string access. Since the private community strings for all the gateway routers were now known to us, by writing a simple script to copy all the router configurations on that network using SNMP and TFTP protocols, we not only compromised the infrastructure of the entire network integration company, but the infrastructure of their clients, as well.

Now that we have gained a basic understanding of SNMP, we can explore one of its main features, the SNMP MIB Tree.

The SNMP Management Information Base (MIB) is a database containing information usually related to network management. The database is organized like a tree, with branches that represent different organizations or network functions. The leaves of the tree (or final endpoints) correspond to specific variable values that can then be accessed and probed by an external user. The IBM Knowledge Center1 contains a wealth of information about the MIB tree.

For example, the following MIB values correspond to specific Microsoft Windows SNMP parameters and contain much more than network-based information:
	
1.3.6.1.2.1.25.1.6.0 	System Processes
1.3.6.1.2.1.25.4.2.1.2 	Running Programs
1.3.6.1.2.1.25.4.2.1.4 	Processes Path
1.3.6.1.2.1.25.2.3.1.4 	Storage Units
1.3.6.1.2.1.25.6.3.1.2 	Software Name
1.3.6.1.4.1.77.1.2.25 	User Accounts
1.3.6.1.2.1.6.13.1.3 	TCP Local Ports

    Table 1 - Windows SNMP MIB values

To scan for open SNMP ports, we can run nmap, using the -sU option to perform UDP scanning and the --open option to limit the output and display only open ports.

kali@kali:~$ sudo nmap -sU --open -p 161 192.168.50.1-254 -oG open-snmp.txt
Starting Nmap 7.92 ( https://nmap.org ) at 2022-03-14 06:02 EDT
Nmap scan report for 192.168.50.151
Host is up (0.10s latency).

PORT    STATE SERVICE
161/udp open  snmp

Nmap done: 1 IP address (1 host up) scanned in 0.49 seconds
...

    Listing 51 - Using nmap to perform a SNMP scan

Alternatively, we can use a tool such as onesixtyone,2 which will attempt a brute force attack against a list of IP addresses. First, we must build text files containing community strings and the IP addresses we wish to scan.

kali@kali:~$ echo public > community
kali@kali:~$ echo private >> community
kali@kali:~$ echo manager >> community

kali@kali:~$ for ip in $(seq 1 254); do echo 192.168.50.$ip; done > ips

kali@kali:~$ onesixtyone -c community -i ips
Scanning 254 hosts, 3 communities
192.168.50.151 [public] Hardware: Intel64 Family 6 Model 79 Stepping 1 AT/AT COMPATIBLE - Software: Windows Version 6.3 (Build 17763 Multiprocessor Free)
...

    Listing 52 - Using onesixtyone to brute force community strings

Once we find SNMP services, we can start querying them for specific MIB data that might be interesting.

We can probe and query SNMP values using a tool such as snmpwalk, provided we know the SNMP read-only community string, which in most cases is "public".

Using some of the MIB values provided in Table 1, we can attempt to enumerate their corresponding values. Let's try the following example against a known machine in the labs, which has a Windows SNMP port exposed with the community string "public". This command enumerates the entire MIB tree using the -c option to specify the community string, and -v to specify the SNMP version number as well as the -t 10 option to increase the timeout period to 10 seconds:

kali@kali:~$ snmpwalk -c public -v1 -t 10 192.168.50.151
iso.3.6.1.2.1.1.1.0 = STRING: "Hardware: Intel64 Family 6 Model 79 Stepping 1 AT/AT COMPATIBLE - Software: Windows Version 6.3 (Build 17763 Multiprocessor Free)"
iso.3.6.1.2.1.1.2.0 = OID: iso.3.6.1.4.1.311.1.1.3.1.3
iso.3.6.1.2.1.1.3.0 = Timeticks: (78235) 0:13:02.35
iso.3.6.1.2.1.1.4.0 = STRING: "admin@megacorptwo.com"
iso.3.6.1.2.1.1.5.0 = STRING: "dc01.megacorptwo.com"
iso.3.6.1.2.1.1.6.0 = ""
iso.3.6.1.2.1.1.7.0 = INTEGER: 79
iso.3.6.1.2.1.2.1.0 = INTEGER: 24
...

    Listing 53 - Using snmpwalk to enumerate the entire MIB tree

Revealed another way, we can use the output above to obtain target email addresses. This information can be used to craft a social engineering attack against the newly-discovered contacts.

To further practice what we've learned, let's explore a few SNMP enumeration techniques against a Windows target. We'll use the snmpwalk command, which can parse a specific branch of the MIB Tree called OID.3

The following example enumerates the Windows users on the dc01 machine.

kali@kali:~$ snmpwalk -c public -v1 192.168.50.151 1.3.6.1.4.1.77.1.2.25
iso.3.6.1.4.1.77.1.2.25.1.1.5.71.117.101.115.116 = STRING: "Guest"
iso.3.6.1.4.1.77.1.2.25.1.1.6.107.114.98.116.103.116 = STRING: "krbtgt"
iso.3.6.1.4.1.77.1.2.25.1.1.7.115.116.117.100.101.110.116 = STRING: "student"
iso.3.6.1.4.1.77.1.2.25.1.1.13.65.100.109.105.110.105.115.116.114.97.116.111.114 = STRING: "Administrator"

    Listing 54 - Using snmpwalk to enumerate Windows users

Our command queried a specific MIB sub-tree that is mapped to all the local user account names.

As another example, we can enumerate all the currently running processes:

kali@kali:~$ snmpwalk -c public -v1 192.168.50.151 1.3.6.1.2.1.25.4.2.1.2
iso.3.6.1.2.1.25.4.2.1.2.1 = STRING: "System Idle Process"
iso.3.6.1.2.1.25.4.2.1.2.4 = STRING: "System"
iso.3.6.1.2.1.25.4.2.1.2.88 = STRING: "Registry"
iso.3.6.1.2.1.25.4.2.1.2.260 = STRING: "smss.exe"
iso.3.6.1.2.1.25.4.2.1.2.316 = STRING: "svchost.exe"
iso.3.6.1.2.1.25.4.2.1.2.372 = STRING: "csrss.exe"
iso.3.6.1.2.1.25.4.2.1.2.472 = STRING: "svchost.exe"
iso.3.6.1.2.1.25.4.2.1.2.476 = STRING: "wininit.exe"
iso.3.6.1.2.1.25.4.2.1.2.484 = STRING: "csrss.exe"
iso.3.6.1.2.1.25.4.2.1.2.540 = STRING: "winlogon.exe"
iso.3.6.1.2.1.25.4.2.1.2.616 = STRING: "services.exe"
iso.3.6.1.2.1.25.4.2.1.2.632 = STRING: "lsass.exe"
iso.3.6.1.2.1.25.4.2.1.2.680 = STRING: "svchost.exe"
...

    Listing 55 - Using snmpwalk to enumerate Windows processes

The command returned an array of strings, each one containing the name of the running process. This information could be valuable as it might reveal vulnerable applications, or even indicate which kind of anti-virus is running on the target.

Similarly, we can query all the software that is installed on the machine:

kali@kali:~$ snmpwalk -c public -v1 192.168.50.151 1.3.6.1.2.1.25.6.3.1.2
iso.3.6.1.2.1.25.6.3.1.2.1 = STRING: "Microsoft Visual C++ 2019 X64 Minimum Runtime - 14.27.29016"
iso.3.6.1.2.1.25.6.3.1.2.2 = STRING: "VMware Tools"
iso.3.6.1.2.1.25.6.3.1.2.3 = STRING: "Microsoft Visual C++ 2019 X64 Additional Runtime - 14.27.29016"
iso.3.6.1.2.1.25.6.3.1.2.4 = STRING: "Microsoft Visual C++ 2015-2019 Redistributable (x86) - 14.27.290"
iso.3.6.1.2.1.25.6.3.1.2.5 = STRING: "Microsoft Visual C++ 2015-2019 Redistributable (x64) - 14.27.290"
iso.3.6.1.2.1.25.6.3.1.2.6 = STRING: "Microsoft Visual C++ 2019 X86 Additional Runtime - 14.27.29016"
iso.3.6.1.2.1.25.6.3.1.2.7 = STRING: "Microsoft Visual C++ 2019 X86 Minimum Runtime - 14.27.29016"
...

    Listing 56 - Using snmpwalk to enumerate installed software

When combined with the running process list we obtained earlier, this information can become extremely valuable for cross-checking the exact software version a process is running on the target host.

Another SNMP enumeration technique is to list all the current TCP listening ports:

kali@kali:~$ snmpwalk -c public -v1 192.168.50.151 1.3.6.1.2.1.6.13.1.3
iso.3.6.1.2.1.6.13.1.3.0.0.0.0.88.0.0.0.0.0 = INTEGER: 88
iso.3.6.1.2.1.6.13.1.3.0.0.0.0.135.0.0.0.0.0 = INTEGER: 135
iso.3.6.1.2.1.6.13.1.3.0.0.0.0.389.0.0.0.0.0 = INTEGER: 389
iso.3.6.1.2.1.6.13.1.3.0.0.0.0.445.0.0.0.0.0 = INTEGER: 445
iso.3.6.1.2.1.6.13.1.3.0.0.0.0.464.0.0.0.0.0 = INTEGER: 464
iso.3.6.1.2.1.6.13.1.3.0.0.0.0.593.0.0.0.0.0 = INTEGER: 593
iso.3.6.1.2.1.6.13.1.3.0.0.0.0.636.0.0.0.0.0 = INTEGER: 636
iso.3.6.1.2.1.6.13.1.3.0.0.0.0.3268.0.0.0.0.0 = INTEGER: 3268
iso.3.6.1.2.1.6.13.1.3.0.0.0.0.3269.0.0.0.0.0 = INTEGER: 3269
iso.3.6.1.2.1.6.13.1.3.0.0.0.0.5357.0.0.0.0.0 = INTEGER: 5357
iso.3.6.1.2.1.6.13.1.3.0.0.0.0.5985.0.0.0.0.0 = INTEGER: 5985
...

    Listing 57 - Using snmpwalk to enumerate open TCP ports

The integer value from the output above represents the current listening TCP ports on the target. This information can be extremely useful as it can disclose ports that are listening only locally and thus reveal a new service that had been previously unknown.
1

(IBM, 2022), https://www.ibm.com/support/knowledgecenter/ssw_aix_71/commprogramming/mib.html ↩︎
2

(Alexander Sotirov, 2008), http://www.phreedom.org/software/onesixtyone/ ↩︎
3

(Wikipedia, 2022), https://en.wikipedia.org/wiki/Object_identifier ↩︎
