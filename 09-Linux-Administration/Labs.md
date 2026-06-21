# Day 09 - Lab: Linux Administration

## Task 1: User Management
```bash
sudo useradd -m labuser
sudo passwd labuser
sudo usermod -aG sudo labuser
cat /etc/passwd | grep labuser
```

## Task 2: Service Management
```bash
sudo apt install nginx -y
systemctl status nginx
systemctl stop nginx
systemctl status nginx
systemctl start nginx
systemctl enable nginx
```
Record: nginx status before/after stop, and confirm it's enabled on boot.

## Task 3: Log Inspection
```bash
journalctl -u nginx --since "10 minutes ago"
sudo tail -20 /var/log/auth.log
```
Record: any recent authentication attempts visible in auth.log.

## Task 4: Disk Usage Check
```bash
df -h
du -sh /var/log
lsblk
```

## Task 5: Schedule a Cron Job
```bash
crontab -e
```
Add this line (runs every 5 minutes, logs current date to a file):
```
*/5 * * * * echo "Cron ran at $(date)" >> /home/$(whoami)/cron-test.log
```
Wait 5-10 minutes, then check:
```bash
cat ~/cron-test.log
```

## Results
| Item | Value |
|---|---|
| labuser created (Y/N) | |
| nginx status after stop | |
| nginx status after start | |
| Auth log entries seen | |
| Disk usage (root partition) | |
| Cron job executed (Y/N) | |

## Cleanup
```bash
sudo userdel -r labuser
crontab -r    # removes all cron jobs for current user, optional
```

## Screenshots
```
![User Created](Screenshots/user-created.png)
![Nginx Status](Screenshots/nginx-status.png)
![Cron Log](Screenshots/cron-log.png)
```

## Lab Summary
Note how long it took for the cron job to run and whether the syntax behaved as expected.
