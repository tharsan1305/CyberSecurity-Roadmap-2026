# Day 67 - Log Analysis

## Goal
Learn to extract security insights from logs - the raw material for SOC analysis, SIEM, and incident response work ahead.

## 1. Log Sources (System, Application, Security)
- **System logs**: OS-level events (reboots, driver failures, kernel messages)
- **Application logs**: app-specific events (web server access, DB queries, app errors)
- **Security logs**: authentication events, privilege use, audit events (Windows Security log, Linux auth.log)
- **Network logs**: firewall logs, VPC Flow Logs, IDS/IPS alerts

## 2. Log Formats (Syslog, JSON, CEF)
- **Syslog**: traditional Unix format - `<priority>timestamp hostname process[pid]: message`
- **JSON**: increasingly common, structured and machine-parseable
- **CEF (Common Event Format)**: standardized format for security tools (ArcSight, many SIEMs)
```
CEF example: CEF:0|Vendor|Product|1.0|100|Login Failed|5|src=192.168.1.10 dst=10.0.0.5 act=blocked
```

## 3. Pattern Recognition
Key patterns to recognize:
- Multiple failed logins -> brute force (Event ID 4625 in Windows, "Failed password" in auth.log)
- Login outside business hours -> anomalous access
- Large outbound data transfer -> possible exfiltration
- New user created -> possible persistence

## 4. Anomaly Detection
Compare observed behavior against a known baseline - significant deviations are anomalies worth investigating.
```bash
# Count failed logins per IP from auth.log
grep "Failed password" /var/log/auth.log | awk '{print $11}' | sort | uniq -c | sort -rn | head -20
```

## Interview Questions
**Q1. Name 3 log sources relevant to security monitoring.**
Windows Security Event Log, Linux auth.log, web server access logs, firewall logs (any 3).
**Q2. What does a spike in Event ID 4625 suggest?**
Multiple failed logon attempts - potential brute-force attack.
**Q3. What is the difference between signature-based and anomaly-based detection?**
Signature-based matches known patterns; anomaly-based detects deviations from a baseline (can catch novel attacks but has more false positives).

## Key Takeaways
- Learned major log sources and their security relevance
- Learned common log formats (Syslog, JSON, CEF)
- Learned key attack patterns visible in logs
- Learned basic anomaly detection with command-line log analysis
