# 94 - n8n Automation
## Overview
n8n is open-source workflow automation, self-hostable and free, ideal for security automation and SOAR-like workflows.

## Install
```bash
docker run -it --rm --name n8n -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n
# Access: http://localhost:5678
```

## Core Nodes
| Node | Security Use |
|------|-------------|
| Webhook | Receive SIEM/EDR alerts |
| Schedule | Daily IOC feed refresh |
| HTTP Request | Call VirusTotal, AbuseIPDB, TheHive |
| IF | Route critical vs low severity |
| Slack/Teams | Notify SOC team |
| Code (JS/Python) | Custom parsing logic |

## Security Workflows

### Phishing Alert Automation
```
Webhook (email gateway alert)
  -> HTTP: Check URL on VirusTotal
  -> IF malicious > 50%:
      -> HTTP: Block URL at proxy
      -> Slack: Alert SOC + create TheHive ticket
  -> ELSE: Queue for manual review
```

### AI Alert Triage
```
Webhook (SIEM alert)
  -> HTTP POST to Claude API: "Rate severity 1-10: {alert}"
  -> IF severity >= 8: PagerDuty + high-priority ticket
  -> ELSE: standard review queue
```

### Daily Threat Intel
```
Schedule (07:00 daily)
  -> HTTP: Pull IOCs from MISP/OTX
  -> Loop: Check each IOC on AbuseIPDB
  -> IF score > 80: add to blocklist
  -> Email: daily IOC digest
```
