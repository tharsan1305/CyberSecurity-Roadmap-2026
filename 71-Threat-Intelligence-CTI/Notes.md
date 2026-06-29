# Day 71 - Threat Intelligence (CTI)

## Goal
Learn Cyber Threat Intelligence (CTI) - using knowledge about attackers and their methods to improve detection and response.

## 1. IOCs (Indicators of Compromise)
Observable artifacts indicating a compromise has occurred or is occurring:
- **IP addresses**: known malicious C2 servers
- **Domain names**: malware C2, phishing domains
- **File hashes (MD5/SHA256)**: known malware samples
- **URLs**: malicious download links
- **Email addresses**: known phishing senders

## 2. Threat Feeds & Sources
- **Open source**: AlienVault OTX, AbuseIPDB, VirusTotal, Shodan, MISP
- **Commercial**: Recorded Future, CrowdStrike Falcon Intelligence
- **Government**: CISA Known Exploited Vulnerabilities (KEV), FBI cyber division advisories

## 3. Attacker TTP Profiling
Moving beyond IOCs to **TTPs (Tactics, Techniques, Procedures)** - harder to change than IOCs, provides longer-lasting detection value. The Pyramid of Pain (David Bianco) visualizes this: blocking IOCs is easy for attackers to bypass; disrupting TTPs causes real pain.

## 4. Intelligence Sharing (STIX/TAXII)
- **STIX (Structured Threat Information eXpression)**: standardized format for sharing threat intelligence
- **TAXII (Trusted Automated eXchange of Intelligence Information)**: protocol for transmitting STIX data between platforms

## Interview Questions
**Q1. What is an IOC, and give 3 examples.**
An Indicator of Compromise - observable evidence of a breach. Examples: known malicious IP, malware file hash, C2 domain.
**Q2. Why are TTPs more valuable than IOCs for detection?**
Attackers can easily change IPs, domains, and hashes; their techniques and procedures are harder to change, so TTP-based detection remains effective longer.
**Q3. What is the purpose of STIX/TAXII?**
STIX provides a standardized format for threat intelligence; TAXII is the protocol for exchanging that intelligence between organizations and platforms.

## Key Takeaways
- Learned IOC types and their role in detection
- Learned major open-source threat intel feeds
- Learned TTP profiling and the Pyramid of Pain concept
- Learned STIX/TAXII for standardized intelligence sharing
