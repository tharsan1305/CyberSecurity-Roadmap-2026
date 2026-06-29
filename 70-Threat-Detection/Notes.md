# Day 70 - Threat Detection

## Goal
Learn modern threat detection approaches - connecting SIEM/Wazuh/Splunk to practical detection engineering.

## 1. Behavioral Analysis
Moving beyond signature-based detection (matching known patterns) to behavioral analysis: detecting what an attacker does, regardless of the specific tool/payload used.
Example: detecting "unusual process spawned by a web server" (a web shell behavior) rather than just "known web shell file hash."

## 2. Signature vs Anomaly-based Detection
| | Signature-based | Anomaly-based |
|---|---|---|
| How | Matches known patterns | Detects deviation from baseline |
| Pros | Fast, low false positives | Catches novel/unknown attacks |
| Cons | Misses unknown/novel attacks | Higher false positives |

Best practice: layer both approaches together.

## 3. Endpoint Detection (EDR)
**EDR (Endpoint Detection and Response)** monitors endpoint activity at the process/file/network level in real time, providing visibility beyond traditional antivirus.
Common commercial tools: CrowdStrike Falcon, SentinelOne, Microsoft Defender for Endpoint.
Open-source: Wazuh (XDR capabilities) covers many EDR use cases.

## 4. Network Traffic Analysis
Analyzing network flow data to detect anomalies (unusual volume, unexpected destinations, C2 communication patterns).
Tools: Zeek (network security monitor), Suricata (IDS/IPS), Arkime (packet capture and analysis).

## Interview Questions
**Q1. Difference between signature-based and anomaly-based detection?**
Signature-based matches known attack patterns; anomaly-based detects deviations from established baselines, enabling detection of novel/unknown attacks.
**Q2. What is EDR and how does it differ from traditional antivirus?**
EDR monitors endpoint behavior continuously (processes, network connections, file changes) rather than just scanning for known malware signatures.
**Q3. What is Zeek used for?**
Network security monitoring - analyzing network traffic to generate logs and detect anomalous communication patterns (C2 beaconing, lateral movement, data exfiltration).

## Key Takeaways
- Learned behavioral detection vs signature-based detection
- Learned EDR concept and example tools
- Learned network traffic analysis tools (Zeek, Suricata, Arkime)
