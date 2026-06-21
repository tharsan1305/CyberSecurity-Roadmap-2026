# Day 52 - SIEM Fundamentals

## Goal
Transition from DevSecOps into the Security Operations phase of the roadmap - SIEM is the central tool of SOC work, log analysis, and threat detection covered extensively in Topics 53-78.

---

## 1. Log Collection & Aggregation

A **SIEM (Security Information and Event Management)** system centralizes log data from across an organization's entire infrastructure - servers, network devices, applications, cloud services - into one searchable platform.

Sources commonly feeding a SIEM:
- Windows Event Logs (Topic 03's Event Viewer concepts, at scale)
- Linux syslog/journalctl (Topic 09's log management, at scale)
- Firewall/network device logs (Topic 24)
- Cloud logs - AWS CloudTrail (Topic 38)
- Application logs

Collection methods: agents installed on endpoints, syslog forwarding, API-based collection from cloud services.

## 2. Correlation Rules

Raw logs alone aren't very useful - a SIEM's value comes from **correlation**: connecting related events across different sources to identify patterns that indicate a security incident.

Example correlation rule logic:
```
IF (5+ failed login events from same source IP within 2 minutes)
AND (followed by 1 successful login from that same IP)
THEN trigger alert: "Possible brute-force success"
```

This connects directly to Event ID 4625 (failed logon) and 4624 (successful logon) from Topic 03 - a SIEM automates pattern detection across these events at scale, instead of manually checking Event Viewer.

## 3. Alerting Mechanisms

When a correlation rule triggers, the SIEM generates an alert - this becomes the starting point for SOC Analysis work (Topic 73).

Alert severity levels (typical): Critical, High, Medium, Low, Informational - based on confidence and potential impact, helping analysts triage what to investigate first.

Alerts can be routed to: a SOC analyst's queue, email/Slack notifications, or automatically trigger SOAR playbooks (Topic 53).

## 4. Dashboard & Visualization

SIEMs provide visual dashboards summarizing security posture: top alert sources, attack trends over time, geographic distribution of login attempts, etc. - making patterns visible that would be very difficult to spot in raw log text.

Popular SIEM platforms (covered hands-on in upcoming topics): Splunk (Topic 69), Wazuh (Topic 68, open-source), Microsoft Sentinel, IBM QRadar, Elastic Security (ELK stack-based).

---

## Interview Questions

**Q1. What is a SIEM, and what core problem does it solve?**
A platform that centralizes and correlates log data from across an organization's infrastructure, solving the problem of manually checking dozens of separate log sources to detect security incidents.

**Q2. What is a correlation rule?**
Logic that connects related events across different log sources/time windows to identify patterns indicating a potential security incident, rather than relying on single isolated log entries.

**Q3. Give an example of a correlation rule for detecting brute-force attacks.**
Multiple failed login attempts from the same source within a short time window, especially if followed by a successful login - suggesting a potential successful brute-force or credential stuffing attack.

**Q4. Why are dashboards/visualizations valuable in a SIEM context?**
They make patterns and trends visible at a glance that would be extremely difficult to identify by reading raw log text manually, supporting faster triage and decision-making.

## Key Takeaways
- Learned what a SIEM is and the log sources that typically feed it
- Learned correlation rules and how they connect to earlier Event ID concepts (Topic 03)
- Learned alerting mechanisms and severity triage
- Learned the role of dashboards/visualization in SIEM platforms
- Set up the foundation for the SOC/Security Operations phase ahead (Topics 53-78)
