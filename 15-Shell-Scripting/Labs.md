# Day 15 - Lab: Shell Scripting Practice

## Task 1: Hello World Script
```bash
cat << 'EOF' > hello.sh
#!/bin/bash
echo "Hello, $(whoami)! Today is $(date)"
EOF
chmod +x hello.sh
./hello.sh
```

## Task 2: Disk Usage Monitor Script
```bash
cat << 'EOF' > disk_monitor.sh
#!/bin/bash
THRESHOLD=80
USAGE=$(df / | tail -1 | awk '{print $5}' | sed 's/%//')

if [ $USAGE -gt $THRESHOLD ]; then
    echo "WARNING: Disk usage is at ${USAGE}%"
else
    echo "Disk usage OK: ${USAGE}%"
fi
EOF
chmod +x disk_monitor.sh
./disk_monitor.sh
```

## Task 3: Log Backup Script
```bash
cat << 'EOF' > backup_logs.sh
#!/bin/bash
BACKUP_DIR="$HOME/log_backups"
DATE=$(date +%Y%m%d_%H%M%S)

mkdir -p $BACKUP_DIR
sudo tar -czf "$BACKUP_DIR/logs_$DATE.tar.gz" /var/log 2>/dev/null
echo "Backup created: $BACKUP_DIR/logs_$DATE.tar.gz"
ls -lh $BACKUP_DIR
EOF
chmod +x backup_logs.sh
./backup_logs.sh
```

## Task 4: Failed SSH Login Counter Script
```bash
cat << 'EOF' > ssh_fail_count.sh
#!/bin/bash
LOGFILE="/var/log/auth.log"
COUNT=$(grep "Failed password" $LOGFILE 2>/dev/null | wc -l)
echo "Failed SSH login attempts: $COUNT"

if [ $COUNT -gt 5 ]; then
    echo "ALERT: High number of failed login attempts detected!"
fi
EOF
chmod +x ssh_fail_count.sh
sudo ./ssh_fail_count.sh
```

## Results
| Item | Value |
|---|---|
| Hello script output | |
| Disk usage shown | |
| Backup file created (Y/N) | |
| Failed SSH attempts count | |

## Screenshots
```
![Disk Monitor Output](Screenshots/disk-monitor.png)
![Backup Script Output](Screenshots/backup-script.png)
![SSH Fail Count](Screenshots/ssh-fail-count.png)
```

## Lab Summary
Note which script you'd actually find useful to keep running on a real system, and why.
