#cybersecurity #active-directory 
#tryhackme

# Active Directory Basics

https://tryhackme.com/room/winadbasics

The most important groups in a domain:

| Security Group | Description |
| --- | --- |
| Domain Admins | Users of this group have administrative privileges over the entire domain. By default, they can administer any computer on the domain, including the DCs. |
| Server Operators | Users in this group can administer Domain Controllers. They cannot change any administrative group memberships. |
| Backup Operators | Users in this group are allowed to access any file, ignoring their permissions. They are used to perform backups of data on computers. |
| Account Operators | Users in this group can create or modify other accounts in the domain. |
| Domain Users | Includes all existing user accounts in the domain. |
| Domain Computers | Includes all existing computers in the domain. |
| Domain Controllers | Includes all existing DCs on the domain. |


## How to RDP from Kali:

### Install Remmina

```bash
sudo apt install remmina 
```


> This might be useful in the future of active directory hacking

The delegated admin can run this command to reset another users password as anything they want:
```powershell
Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -verbose 
```

This part will prompt that user to reset their password at login:
```PowerShell
Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose 
```


TryHackMe had issues, had to change the line ``cipher AES-256-CBC`` to ``data-ciphers AES-256-CBC``


<iframe width="560" height="315" src="https://www.youtube.com/embed/lC0HEPegPMs?start=2720" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
