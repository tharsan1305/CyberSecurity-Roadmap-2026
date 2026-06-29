# 74 - Incident Response

## Overview
Incident Response (IR) is the structured process for managing security incidents. The goal is to limit damage, preserve evidence, restore normal operations, and prevent recurrence.

---

## 1. IR Lifecycle – PICERL Model

### Phase 1: Preparation
- Build IR team with defined roles (IR Lead, Forensics, Comms)
- Develop and regularly test playbooks
- Deploy detection tools: SIEM, EDR, NDR
- Create communication trees and escalation paths
- Prepare IR toolkit: forensic software, USB drives, checklists

### Phase 2: Identification / Detection
- Sources: SIEM alerts, EDR, IDS/IPS, threat intel, user reports
- Determine: Is this a real incident or false positive?
- Classify the incident type and assign severity

### Phase 3: Containment
**Short-term:** Isolate affected systems, block IPs/domains, disable compromised accounts
**Long-term:** Patch vulnerabilities, change all credentials in scope, tighten firewall rules

### Phase 4: Eradication
- Remove malware and attacker-created artifacts
- Delete rogue accounts
- Close the initial access vector
- Confirm clean state with multiple AV/EDR scans

### Phase 5: Recovery
- Restore systems from verified clean backups
- Re-enable services in controlled sequence
- Monitor intensively for 48–72 hours post-recovery

### Phase 6: Lessons Learned
- Post-incident review within 2 weeks
- Document full timeline, impact, response quality
- Update playbooks, detection rules, and security controls

---

## 2. Incident Classification

| Type               | Examples                              |
|--------------------|---------------------------------------|
| Malware Infection  | Ransomware, Trojan, Worm, Keylogger   |
| Phishing           | Credential harvesting, BEC            |
| Unauthorized Access| Brute force, stolen credentials       |
| Data Exfiltration  | Insider threat, APT exfil             |
| DDoS               | Volumetric, application-layer         |
| Insider Threat     | Data theft, sabotage                  |
| Supply Chain       | Compromised vendor/software           |

---

## 3. Playbook Development

### Phishing Playbook (Example)
```
TRIGGER: User reports suspicious email

1. TRIAGE
   - Collect full email headers
   - Analyze: sender, subject, links, attachments
   - Check URLs via VirusTotal / URLScan.io
   - Check attachments via Any.run / Hybrid Analysis
   - Determine: Did user click? Did user enter credentials?

2. CONTAINMENT
   - Block sender domain in email gateway
   - Remove email from ALL mailboxes (organization-wide)
   - Reset password if credentials entered
   - Enable/verify MFA on affected account

3. ERADICATION
   - Scan affected endpoint with EDR
   - Remove any malware dropped via attachment

4. RECOVERY
   - Restore normal access after password reset + MFA
   - Brief user on phishing recognition

5. DOCUMENTATION
   - Log all IOCs: sender domain, URL, file hash
   - Open incident ticket with full timeline
   - Notify management if credentials were compromised
```

---

## 4. Communication Protocols

### Internal Communication
- SOC → IR Lead → SOC Manager → CISO → Legal/Compliance → HR (if insider)
- Use out-of-band channels if primary email/Slack is compromised

### External Communication
- **Law enforcement:** If criminal activity (ransomware, fraud)
- **Regulatory body:** GDPR – 72 hours; HIPAA – 60 days; PCI-DSS – immediately
- **Customers:** Data breach notification letters
- **Cyber insurance:** Notify insurer before paying ransom or hiring IR firm

### Notification Template
```
Subject: [CONFIDENTIAL] Security Incident – [Date] – [Severity]

Affected Systems    :
Summary             :
Current Status      :
Actions Taken       :
Next Steps          :
Point of Contact    :
Estimated Resolution:
```

---

## 5. Post-Incident Review

### Key Review Questions
1. When did the incident start and how long until detected?
2. What was the root cause and initial access vector?
3. What was the business impact (downtime, data loss, cost)?
4. What detection or prevention controls failed?
5. What worked well in the response?
6. What needs to be improved?

### Deliverables
- Full Incident Report (for leadership)
- IOC List shared with threat intelligence teams
- Lessons Learned Document
- Updated Playbooks and Detection Rules
