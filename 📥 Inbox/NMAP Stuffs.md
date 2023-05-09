To conduct a SYN stealth scan of your target IP range using Nmap and save the output to a file, follow these steps:

1. Open a terminal on your Linux machine.

2. Run the Nmap command with the `-sS` flag for SYN stealth scanning, the target IP range (with the third octet replaced by 50 as requested), and `-oN` to save the output to a file. For example, if you want to scan the range 192.168.50.1-255, you can use:

```bash
nmap -sS 192.168.50.1-255 -oN nmap_output.txt
```

3. Once the scan is complete, you can use `grep` to filter the results and show machines that are online. To do this, run:

```bash
grep -B3 'Host is up' nmap_output.txt
```

4. To find the host with port 25 open, use another `grep` command:

```bash
grep -B3 '25/open' nmap_output.txt
```

This command will display the information for the host with port 25 open. The IP address of the host will be in the line above the port information.

Please ensure you have permission to perform the port scanning on the target IP range, as unauthorized scanning may be illegal or against network policies.