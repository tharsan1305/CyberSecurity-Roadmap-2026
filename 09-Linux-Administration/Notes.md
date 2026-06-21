# Day 09 - Linux Administration

## Goal
Learn day-to-day Linux system administration tasks - user management, service control, log management, disk management, and scheduled jobs.

---

## 1. User & Group Management

```bash
sudo useradd -m newuser           # create user with home directory
sudo passwd newuser                 # set password
sudo usermod -aG sudo newuser        # add user to sudo group
sudo userdel -r newuser               # delete user and home directory

groupadd devteam
usermod -aG devteam newuser
```

Key files:
- `/etc/passwd` - user account info
- `/etc/shadow` - hashed passwords (root-readable only)
- `/etc/group` - group definitions

## 2. Service Management (systemctl)

```bash
systemctl status nginx
systemctl start nginx
systemctl stop nginx
systemctl restart nginx
systemctl enable nginx     # start on boot
systemctl disable nginx
```

## 3. Log Management

```bash
journalctl                   # view systemd logs
journalctl -u nginx           # logs for a specific service
journalctl -f                  # follow logs live (like tail -f)
journalctl --since "1 hour ago"

tail -f /var/log/syslog        # follow a traditional log file
tail -100 /var/log/auth.log     # last 100 lines of auth log
```

`/var/log/auth.log` (Debian/Ubuntu) or `/var/log/secure` (RHEL/CentOS) tracks authentication events - directly relevant to security monitoring.

## 4. Disk & Storage Management

```bash
df -h                  # disk space usage, human-readable
du -sh /var/log          # size of a specific directory
lsblk                     # list block devices
fdisk -l                   # list disk partitions (requires sudo)
mount /dev/sdb1 /mnt        # mount a device
```

## 5. Cron Jobs

Cron schedules recurring tasks.

```bash
crontab -e           # edit current user's cron jobs
crontab -l            # list current user's cron jobs
```

Cron syntax:
```
* * * * * command
│ │ │ │ │
│ │ │ │ └── day of week (0-6)
│ │ │ └──── month (1-12)
│ │ └────── day of month (1-31)
│ └──────── hour (0-23)
└────────── minute (0-59)
```

Example: run a backup script every day at 2 AM:
```
0 2 * * * /home/user/backup.sh
```

---

## Interview Questions

**Q1. Where are user passwords stored (hashed) in Linux?**
`/etc/shadow`, which is readable only by root for security.

**Q2. How do you view logs for a specific systemd service?**
`journalctl -u <servicename>`

**Q3. What does `df -h` show, and how is it different from `du -sh`?**
`df -h` shows overall disk space usage per filesystem/mount point; `du -sh` shows the size of a specific file or directory.

**Q4. Write a cron expression to run a script every day at 2 AM.**
`0 2 * * * /path/to/script.sh`

## Key Takeaways
- Learned Linux user/group management commands and key files
- Learned systemctl service management
- Learned log management with journalctl and traditional log files
- Learned disk/storage inspection commands
- Learned cron job syntax and scheduling
