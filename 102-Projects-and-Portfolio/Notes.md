# 102 - Projects & Portfolio
## Overview
Real projects + strong portfolio = job offers. This topic covers project ideas, GitHub setup, and career prep.

## Project 1: SOC Automation with SOAR
**Stack**: n8n + Wazuh + VirusTotal + TheHive + Slack
**Features**:
- Webhook receives SIEM alerts
- Auto-enriches IOCs via VirusTotal and AbuseIPDB
- Creates TheHive case with all evidence
- Notifies SOC via Slack with severity and MITRE technique
- Auto-closes confirmed false positives

## Project 2: AI Security Scanner
**Stack**: Python + Claude API + LangChain + Streamlit
**Features**:
- Upload Nessus/OpenVAS XML -> AI prioritizes findings by real risk
- Paste logs -> AI identifies attack patterns + MITRE mapping
- Chat interface to ask questions about findings
- Export AI-generated executive summary PDF

## Project 3: RAG Threat Intelligence Bot
**Stack**: Python + LangChain + ChromaDB + Claude API + Streamlit
**Features**:
- Ingest CVEs, threat reports, IOC feeds, MITRE ATT&CK
- Natural language queries: 'What TTPs does APT-29 use?'
- Source citations with every answer
- Continuous ingestion pipeline for new intel

## Project 4: LangGraph Multi-Agent IR System
**Stack**: LangGraph + Claude API + Security APIs + TheHive
**Agents**:
- Triage Agent: classify type and severity
- Investigation Agent: enrich IOCs, map to MITRE
- Containment Agent: recommend + execute containment (with human approval)
- Reporting Agent: generate full IR report

## GitHub Portfolio Structure
```
github.com/yourusername/
  CyberSecurity-Roadmap/      <- This repo!
  soc-automation-soar/        <- Project 1
  ai-security-scanner/        <- Project 2
  threat-intel-rag-bot/       <- Project 3
  langgraph-security-agents/  <- Project 4
```

## Every Repo Needs
- README.md with: overview, architecture diagram, setup steps, demo GIF/screenshot
- requirements.txt or Dockerfile
- .env.example (never commit real API keys)
- Clean, commented, well-structured code

## CTF Platforms
| Platform | Level | Link |
|----------|-------|------|
| PicoCTF | Beginner | picoctf.org |
| TryHackMe | Guided | tryhackme.com |
| HackTheBox | Pro | hackthebox.com |
| CTFtime | Calendar | ctftime.org |

## Bug Bounty
| Platform | Programs | Payouts |
|----------|----------|---------|
| HackerOne | 1000s | 50-1M+ USD |
| Bugcrowd | Enterprise | Varies |
| INTIGRITI | European | Varies |

## Target Certifications
```
Foundation: CompTIA Security+
Analyst:    CompTIA CySA+ or Microsoft SC-200
IR/DFIR:    GCIH or GCFA (GIAC)
Advanced:   CISSP or OSCP
AI Security: Portfolio projects (no cert yet - YOU are the credential)
```
