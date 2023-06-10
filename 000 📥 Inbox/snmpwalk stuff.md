To query the Windows host's SNMP server for interface names and translate any hexadecimal strings into ASCII, follow these steps:

1. Install `snmpwalk` if not already installed:

```bash
sudo apt-get install snmp
```

2. Use `snmpwalk` with the `-Oa` parameter to query the Windows host's SNMP server for interface names:

```bash
snmpwalk -Oa -c <community_string> -v 2c <IP_address> 1.3.6.1.2.1.2.2.1.2
```

Replace `<community_string>` with the SNMP community string you found when you scanned the target network, and `<IP_address>` with the IP address of the Windows host running the SNMP server.

3. Review the output of the `snmpwalk` command. The first interface name listed in the output should be displayed as an ASCII string. The interface names may look something like "Ethernet0" or "Local Area Connection".

Please ensure you have permission to interact with the target IP range, as unauthorized actions may be illegal or against network policies.