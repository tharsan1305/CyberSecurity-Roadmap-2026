# Day 67 - Lab: Log Analysis

## Objective
Analyze sample log files to identify security events.

## Task 1: Generate a Sample Auth Log
```bash
cat << 'EOF' > sample_auth.log
Jun 21 10:00:01 server sshd[1234]: Failed password for root from 45.33.32.156 port 54321 ssh2
Jun 21 10:00:02 server sshd[1234]: Failed password for root from 45.33.32.156 port 54322 ssh2
Jun 21 10:00:03 server sshd[1234]: Failed password for admin from 45.33.32.156 port 54323 ssh2
Jun 21 10:00:05 server sshd[1235]: Accepted password for labuser from 192.168.1.50 port 22 ssh2
Jun 21 10:01:00 server sshd[1234]: Failed password for root from 198.51.100.1 port 12345 ssh2
EOF
```

## Task 2: Count Failed Logins Per IP
```bash
grep "Failed password" sample_auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -rn
```

## Task 3: Extract Successful Logins Only
```bash
grep "Accepted" sample_auth.log
```

## Task 4: Detect Brute Force (More Than 2 Attempts from Same IP)
```bash
grep "Failed password" sample_auth.log | awk '{print $(NF-3)}' | sort | uniq -c | awk '$1 > 2 {print "ALERT: Brute force from " $2 " (" $1 " attempts)"}'
```

## Results
| Item | Value |
|---|---|
| Total failed login attempts | |
| Attacking IPs identified | |
| Brute force alert triggered (Y/N) | |
| Successful logins found | |

## Lab Summary
Note how this command-line log analysis connects directly to what a SIEM does automatically at scale.
