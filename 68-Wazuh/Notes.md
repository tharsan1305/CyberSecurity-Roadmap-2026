# Day 68 - Wazuh

## Goal
Learn Wazuh - the most widely used open-source SIEM/XDR platform, combining log analysis, file integrity monitoring, and alerting.

## 1. Agent Deployment
Wazuh uses a manager-agent architecture:
- **Manager**: central server receiving/analyzing data
- **Agent**: installed on monitored endpoints, collects and forwards logs/events

```bash
# Install Wazuh Manager (Docker quickstart)
docker-compose -f wazuh-docker/single-node/docker-compose.yml up -d

# Install agent on Ubuntu endpoint
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | apt-key add -
apt install wazuh-agent -y
WAZUH_MANAGER="<manager-ip>" systemctl start wazuh-agent
```

## 2. Rule Configuration
Wazuh detects events using rules (XML format). Each rule has an ID, level (severity 1-15), and conditions.

```xml
<rule id="100001" level="10">
  <if_matched_sid>5710</if_matched_sid>
  <description>Multiple SSH authentication failures (possible brute force)</description>
  <group>authentication_failures,</group>
</rule>
```

Higher level = more severe. Level 12+ typically triggers immediate alerts.

## 3. File Integrity Monitoring (FIM)
Wazuh monitors specified files/directories for changes, alerting when files are modified/added/deleted.

```xml
<!-- In ossec.conf on agent -->
<syscheck>
  <directories check_all="yes">/etc,/usr/bin,/bin</directories>
</syscheck>
```

Relevant for detecting: unauthorized config changes, malware planting files, attacker persistence mechanisms.

## 4. Alert Dashboard
Wazuh ships with a Kibana/OpenSearch dashboard showing: alert trends, top rules triggered, agent status, and FIM events - your first real SIEM dashboard experience.

## Interview Questions
**Q1. What architecture does Wazuh use?**
Manager-agent: agents collect/forward data from endpoints to the central manager for analysis.
**Q2. What is File Integrity Monitoring (FIM) used for?**
Detecting unauthorized changes to critical files/directories (malware, attacker persistence, config tampering).
**Q3. What does a Wazuh rule level indicate?**
The severity of the detected event - higher levels (12+) trigger immediate alerts.

## Key Takeaways
- Learned Wazuh manager-agent architecture and deployment
- Learned rule structure and severity levels
- Learned File Integrity Monitoring configuration and use cases
- Learned Wazuh dashboard for alert visualization
