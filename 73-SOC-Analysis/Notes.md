# 73 - SOC Analysis

## Overview
A Security Operations Center (SOC) is a centralized unit responsible for monitoring, detecting, analyzing, and responding to cybersecurity threats 24/7. It is the heartbeat of an organization's defensive security posture.

---

## 1. Alert Triage (Tier 1 / Tier 2)

### Tier 1 – Alert Monitoring
- First responders to incoming SIEM, EDR, and IDS/IPS alerts
- Duties: Monitor queues, filter false positives, categorize severity, escalate to Tier 2

### Tier 2 – Incident Investigation
- Investigate escalated alerts, correlate multi-source events
- Perform threat hunting based on IOCs, determine scope, recommend containment

### Triage Workflow
```
Alert Received → Validate (FP/TP?) → Categorize Severity → Investigate → Escalate or Close
```

### Severity Levels
| Level    | Description                          | Response Time |
|----------|--------------------------------------|---------------|
| Critical | Active breach / ransomware           | Immediate     |
| High     | Privilege escalation / data exfil    | < 1 hour      |
| Medium   | Suspicious login / policy violation  | < 4 hours     |
| Low      | Informational / minor anomaly        | < 24 hours    |

---

## 2. SIEM Monitoring

### What is SIEM?
Security Information and Event Management — aggregates, correlates, and analyzes logs from across the environment to detect threats.

### Popular SIEM Tools
| Tool               | Notes                                   |
|--------------------|-----------------------------------------|
| Splunk             | Industry standard, powerful SPL language|
| IBM QRadar         | Enterprise grade with threat intel      |
| Microsoft Sentinel | Cloud-native, integrates with Azure     |
| Elastic SIEM       | Open-source, ELK stack                  |
| Wazuh              | Free open-source SIEM + EDR             |

### Key SIEM Functions
- Log aggregation from firewalls, servers, endpoints, cloud
- Real-time event correlation and alerting
- Dashboard visualization and reporting
- Compliance log retention

### Splunk Example Query (Brute Force Detection)
```spl
index=windows EventCode=4625
| stats count by src_ip, user
| where count > 10
| sort -count
```

---

## 3. Escalation Procedures

### When to Escalate
- Confirmed malware infection on endpoint
- Unauthorized access to sensitive/privileged systems
- Detected data exfiltration
- Ransomware indicators (mass file encryption)
- Insider threat activity

### Escalation Path
```
Tier 1 Analyst → Tier 2 Analyst → IR Team → SOC Manager → CISO → Legal/PR
```

### Escalation Checklist
- [ ] Document all evidence and timestamps
- [ ] Identify affected systems and user accounts
- [ ] Preserve logs and forensic artifacts
- [ ] Open formal ticket with severity rating
- [ ] Notify stakeholders per communication tree

---

## 4. Daily SOC Workflow

### Morning Shift Start
- Review overnight alerts and open tickets
- Check threat intelligence feeds (MISP, OTX, ISAC feeds)
- Confirm all monitoring tools are healthy (SIEM, EDR, firewall)

### During Shift
- Monitor alert queues continuously
- Investigate and document suspicious events
- Update open ticket statuses
- Collaborate with Tier 2 on complex events

### End of Shift Handover
- Brief incoming team on open incidents
- Document unresolved alerts with current status
- Update daily SOC metrics report

### SOC KPIs to Track
| KPI                    | Target              |
|------------------------|---------------------|
| MTTD (Mean Time to Detect) | < 60 minutes   |
| MTTR (Mean Time to Respond)| < 4 hours      |
| False Positive Rate        | < 30%          |
| Alerts Closed per Analyst  | 80%+ per shift |

---

## Key Terms
| Term  | Definition                              |
|-------|-----------------------------------------|
| IOC   | Indicator of Compromise                 |
| TTP   | Tactics, Techniques, and Procedures     |
| SIEM  | Security Information & Event Management |
| EDR   | Endpoint Detection and Response         |
| MTTD  | Mean Time to Detect                     |
| MTTR  | Mean Time to Respond                    |
| FP/TP | False Positive / True Positive          |
| NDR   | Network Detection and Response          |
