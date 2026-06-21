# Day 10 - Lab: Linux Server Administration

## Task 1: SSH Key-Based Authentication
```bash
ssh-keygen -t ed25519 -C "lab@example.com"
ssh-copy-id labuser@<server-ip>
ssh labuser@<server-ip>
```
Verify you can log in without a password prompt.

## Task 2: Harden SSH Config
Edit `/etc/ssh/sshd_config`:
```
PermitRootLogin no
PasswordAuthentication no
```
```bash
sudo systemctl restart sshd
```
Test: confirm root login and password-based login are now refused.

## Task 3: Install and Test Nginx
```bash
sudo apt install nginx -y
systemctl status nginx
curl localhost
```
Edit the default page at `/var/www/html/index.nginx-debian.html` and refresh `curl localhost` to see the change.

## Task 4: Configure UFW Firewall
```bash
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw enable
sudo ufw status verbose
```

## Task 5: Create a Backup
```bash
sudo tar -czvf etc-backup.tar.gz /etc
ls -lh etc-backup.tar.gz
```

## Results
| Item | Value |
|---|---|
| SSH key login successful (Y/N) | |
| Root login blocked (Y/N) | |
| Nginx serving content (Y/N) | |
| UFW status | |
| Backup file size | |

## Screenshots
```
![SSH Key Login](Screenshots/ssh-key-login.png)
![Nginx Running](Screenshots/nginx-running.png)
![UFW Status](Screenshots/ufw-status.png)
```

## Lab Summary
Note any connection issues after hardening SSH and how you resolved them (a common real mistake is locking yourself out - always test in a second session before closing the first).
