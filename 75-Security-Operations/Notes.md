# 75 - Security Operations (SecOps)

## Overview
Security Operations covers the day-to-day operational tasks that keep an organization's security running smoothly. SecOps bridges the gap between security engineering and active defense.

---

## 1. Daily Operational Tasks

### Morning Checks
- Verify SIEM, EDR, firewall, and IDS/IPS are fully operational
- Review overnight alert queue and pending tickets
- Check threat intelligence feeds for new IOCs
- Confirm backup jobs completed successfully
- Review vulnerability scanner results

### Ongoing Tasks
- Monitor dashboards for anomalies
- Investigate and close or escalate alerts
- Coordinate patch deployment with IT teams
- Manage firewall rule change requests
- Respond to security tool false positives (tune rules)

### End-of-Day Tasks
- Update all open ticket statuses
- Document any unresolved security events
- Submit daily metrics report to SOC Manager

---

## 2. Shift Handover Processes

### What to Include in Handover
- Open incidents and their current status
- Critical alerts received during shift
- Any tool outages or degraded monitoring coverage
- Pending actions for next shift
- Any threat intelligence updates

### Handover Template
```
SHIFT HANDOVER – [Date] [Shift Time]
Outgoing Analyst  :
Incoming Analyst  :

OPEN INCIDENTS
  1. [Ticket #] – [Brief description] – Status: [In Progress / Escalated]

ALERTS OF NOTE
  - [Alert summary and current status]

TOOL STATUS
  - SIEM: [ OK / Degraded ]
  - EDR:  [ OK / Degraded ]
  - IDS:  [ OK / Degraded ]

PENDING ACTIONS FOR NEXT SHIFT
  -

THREAT INTEL UPDATES
  - New IOCs / CVEs to watch:
```

---

## 3. Tool Management

### Security Tool Stack Overview
| Category      | Tools                                       |
|---------------|---------------------------------------------|
| SIEM          | Splunk, Sentinel, QRadar, Elastic           |
| EDR           | CrowdStrike Falcon, SentinelOne, Defender   |
| Firewall/NGFW | Palo Alto, Fortinet, Cisco Firepower        |
| IDS/IPS       | Snort, Suricata, Zeek                       |
| Vuln Scanner  | Tenable Nessus, Qualys, OpenVAS             |
| SOAR          | Splunk SOAR, IBM SOAR, Palo Alto XSOAR     |
| Threat Intel  | MISP, OTX, ThreatConnect, Recorded Future  |

### Tool Health Checks
- Confirm log ingestion is current (no gaps in SIEM)
- Verify EDR agents are online and reporting
- Check IDS/IPS signature updates are current
- Confirm firewall policies are enforcing correctly

---

## 4. Metrics & Reporting

### Daily Metrics to Track
| Metric                  | Formula / Source                   |
|-------------------------|------------------------------------|
| Total Alerts            | SIEM dashboard                     |
| True Positive Rate      | TP / Total Alerts × 100            |
| False Positive Rate     | FP / Total Alerts × 100            |
| Escalation Rate         | Escalations / Total Alerts × 100   |
| MTTD                    | Avg time from event to detection   |
| MTTR                    | Avg time from detection to resolve |

### Weekly SOC Report Template
```
WEEKLY SECURITY OPERATIONS REPORT
Period      :
Prepared By :

1. EXECUTIVE SUMMARY
   [2-3 line summary of the week]

2. INCIDENT SUMMARY
   Total Incidents  :
   Critical         :
   High             :
   Medium/Low       :
   Closed           :

3. ALERT STATISTICS
   Total Alerts     :
   True Positives   :
   False Positives  :
   FP Rate          :

4. TOP THREATS OBSERVED
   -

5. TOOL HEALTH
   -

6. RECOMMENDATIONS
   -
```
