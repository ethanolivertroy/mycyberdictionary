---

title: "Linux Change Hostname"

date: 2020-01-18

draft: false

tags: ["Linux"]

categories: ["Linux"]

---

# How to Change the Linux Hostname

  > [!abstract]  
  > Basically how to change the name of your Linux box and update it in the places you need to as to not break anything 😅.

Ubuntu change hostname command

The procedure to change the computer name on Ubuntu Linux:

  

1. Edit /etc/hostname using nano

```bash

sudo nano /etc/hostname

```

2. Delete the old name and write a new one

3. Edit /etc/hosts

```bash

sudo nano /etc/hosts

```

4. Replace old name with the new one

5. Reboot and check that it worked

```bash

sudo reboot

```