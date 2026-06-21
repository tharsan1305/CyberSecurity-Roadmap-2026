# Day 10 - Linux Server Administration

## Goal
Learn to secure and manage Linux servers in production-like conditions - SSH hardening, web servers, firewalls, monitoring, and backups.

---

## 1. SSH Configuration & Hardening

SSH config file: `/etc/ssh/sshd_config`

Common hardening steps:
```
PermitRootLogin no              # disable direct root login
PasswordAuthentication no        # force key-based auth only
Port 2222                         # change default port (security through obscurity, minor benefit)
AllowUsers labadmin                # restrict which users can SSH in
```

After editing: `sudo systemctl restart sshd`

SSH key-based authentication:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
ssh-copy-id user@remote-server
ssh user@remote-server    # now connects without password
```

## 2. Web Servers (Apache, Nginx)

### Nginx
```bash
sudo apt install nginx -y
systemctl status nginx
```
Config location: `/etc/nginx/sites-available/`, enabled via symlink in `/etc/nginx/sites-enabled/`

### Apache
```bash
sudo apt install apache2 -y
```
Config location: `/etc/apache2/sites-available/`

Both serve web content from `/var/www/html` by default.

## 3. Firewall (iptables, ufw)

### ufw (Uncomplicated Firewall) - simpler frontend for iptables
```bash
sudo ufw enable
sudo ufw allow 22/tcp        # allow SSH
sudo ufw allow 80,443/tcp     # allow HTTP/HTTPS
sudo ufw deny 23                # deny telnet
sudo ufw status verbose
```

### iptables (lower-level, more granular)
```bash
sudo iptables -L -v               # list rules
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -j DROP     # default deny (place last)
```

## 4. Server Monitoring

```bash
top / htop          # live resource usage
vmstat 1               # virtual memory stats, refreshed every second
iostat                  # disk I/O stats
netstat -tulnp           # listening ports and associated processes
```

## 5. Backup & Recovery

```bash
tar -czvf backup.tar.gz /etc /var/www      # create compressed backup
tar -xzvf backup.tar.gz -C /restore/path     # restore

rsync -avz /source/ user@remote:/destination/   # sync/backup to remote server
```

---

## Interview Questions

**Q1. What's the main SSH hardening step to prevent brute-force root login attempts?**
Setting `PermitRootLogin no` and enforcing key-based authentication (`PasswordAuthentication no`) in `sshd_config`.

**Q2. Difference between ufw and iptables?**
ufw is a simplified frontend that generates iptables rules underneath; iptables offers more granular, lower-level control but is more complex to configure directly.

**Q3. Where is web content typically served from by default in Nginx/Apache?**
`/var/www/html`

**Q4. What does `rsync -avz` do?**
Synchronizes files/directories to a destination (local or remote) with archive mode, verbose output, and compression - commonly used for backups.

## Key Takeaways
- Learned SSH hardening: key-based auth, disabling root login
- Learned Nginx and Apache basics and config locations
- Learned firewall configuration with ufw and iptables
- Learned server monitoring tools and commands
- Learned backup/restore with tar and rsync
