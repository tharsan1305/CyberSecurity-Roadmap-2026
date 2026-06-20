# Day 25 - NOC (Network Operations Center)

## Goal
Understand how organizations monitor network health and uptime, and the operational workflows of a NOC team - a common entry-level role in IT/networking careers.

---

## 1. What is a NOC?

A centralized team/location responsible for monitoring, maintaining, and troubleshooting an organization's network infrastructure 24/7 to ensure uptime and performance.

NOC vs SOC (important distinction, since SOC comes later in this roadmap):
- **NOC**: focuses on network performance, uptime, availability
- **SOC**: focuses on security threats, incidents, attacks

Some organizations combine them; many keep them separate with different tools and KPIs.

## 2. Network Monitoring Tools

### Nagios
Open-source monitoring tool that checks host/service availability and alerts on failures. Uses plugins to check various metrics (CPU, disk, ping, port status).

### Zabbix
Open-source monitoring platform with built-in dashboards, alerting, and auto-discovery of network devices. More modern UI/feature set than Nagios in many deployments.

Both tools work on a similar principle: agents or agentless checks (SNMP, ICMP) collect metrics from devices, compare against thresholds, and trigger alerts.

## 3. Uptime & Performance Monitoring

Key metrics NOC teams track:
- **Uptime/Downtime** - percentage of time a service is available (e.g., "99.9% uptime")
- **Latency** - delay in data transmission
- **Packet Loss** - percentage of packets that fail to reach destination
- **Bandwidth Utilization** - how much of available capacity is in use

SLA (Service Level Agreement) targets are often tied directly to these metrics - e.g., "99.9% uptime guaranteed."

## 4. Ticketing Systems

NOC teams use ticketing systems (e.g., Jira Service Management, ServiceNow, Zendesk) to:
- Log incidents reported by monitoring tools or users
- Track resolution status
- Maintain an audit trail of issues and fixes

A typical ticket lifecycle: New → Assigned → In Progress → Resolved → Closed

## 5. Escalation Procedures

When a Tier 1 NOC analyst can't resolve an issue within a defined time/scope, it escalates:
```
Tier 1 (initial triage, basic fixes)
   ↓ (if unresolved)
Tier 2 (deeper technical troubleshooting)
   ↓ (if unresolved)
Tier 3 (senior engineers, vendor escalation)
```

Escalation procedures typically define: time thresholds for escalation, who to contact, and what information must be documented before escalating.

---

## Interview Questions

**Q1. Difference between NOC and SOC?**
NOC focuses on network performance and uptime; SOC focuses on security threats and incident response.

**Q2. What is an SLA?**
Service Level Agreement - a commitment defining expected service performance, often tied to uptime percentage.

**Q3. What's the purpose of a ticketing system in NOC operations?**
To log, track, and maintain an audit trail of incidents from detection through resolution.

**Q4. What happens when a Tier 1 analyst can't resolve an issue?**
It gets escalated to Tier 2 (or further to Tier 3) based on defined escalation procedures and time thresholds.

## Key Takeaways
- Understood NOC's role and how it differs from SOC
- Learned common monitoring tools: Nagios, Zabbix
- Learned key uptime/performance metrics tracked by NOC teams
- Understood ticketing system workflows and escalation tiers
