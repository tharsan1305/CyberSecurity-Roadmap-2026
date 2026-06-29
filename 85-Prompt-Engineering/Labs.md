# 85 - Prompt Engineering - Labs

## Lab 1: Zero-Shot vs Few-Shot Comparison

### Objective
Test the difference between zero-shot and few-shot prompting for security log analysis.

### Test Prompt A (Zero-Shot)
```
Classify the severity of this security event:
"Windows Defender detected and quarantined Trojan.GenericKD.12345 on WORKSTATION-7"
```

### Test Prompt B (Few-Shot)
```
Classify the severity of security events. Examples:

Event: "Failed SSH login from 10.0.0.5 - 3 attempts"
Severity: LOW - Reason: Few attempts, internal IP, no success

Event: "Ransomware detected, 1000 files encrypted"
Severity: CRITICAL - Reason: Active encryption, likely spreading

Event: "New admin user created outside business hours"
Severity: HIGH - Reason: Unauthorized privileged access, unusual timing

Now classify:
Event: "Windows Defender detected and quarantined Trojan.GenericKD.12345 on WORKSTATION-7"
Severity:
```

Compare the outputs — which is more consistent and actionable?

---

## Lab 2: Build a Security Analysis Prompt

### Objective
Create a reusable prompt template for analyzing SIEM alerts.

### Template to Fill
```
SYSTEM: [Define the AI's role and expertise]

TASK: Analyze the following SIEM alert and provide:
1. Alert severity (Critical/High/Medium/Low) with justification
2. MITRE ATT&CK Tactic and Technique
3. Likely attack scenario explanation
4. Top 3 immediate investigation steps
5. Recommended containment action

FORMAT: Respond in this exact structure:
SEVERITY: [level]
MITRE: [Tactic] → [Technique ID] – [Technique Name]
SCENARIO: [2-3 sentence explanation]
INVESTIGATION:
  1. [Step]
  2. [Step]
  3. [Step]
CONTAINMENT: [Action]

ALERT DATA:
[Paste your alert here]
```

Test this template with 3 different sample alerts from MalwareBazaar or public CTF logs.

---

## Lab 3: Chain-of-Thought for Incident Analysis

### Objective
Use CoT prompting to analyze a multi-stage attack scenario.

### Prompt
```
You are a threat intelligence analyst. Think step by step to analyze this sequence of events
and determine what type of attack occurred and what the attacker's goal was.

Events:
1. 09:14 – Phishing email opened by user@company.com, attachment downloaded
2. 09:16 – Word document opened, macro executed
3. 09:17 – PowerShell spawned from Word.exe, downloaded file from 185.220.x.x
4. 09:18 – New scheduled task created: "WindowsUpdate" running malware.exe
5. 09:45 – Outbound connection to 185.220.x.x every 60 seconds (C2 beaconing)
6. 11:30 – LSASS.exe memory read by malware.exe (credential dumping)
7. 12:00 – SMB lateral movement to 5 other workstations

Step by step, identify:
- Initial access method
- Execution technique
- Persistence mechanism
- Command and control
- Credential access
- Lateral movement
- MITRE ATT&CK techniques for each phase
- Likely attacker objective
```

---

## Practice Challenges
- [ ] Write 5 different prompts for the same security task, compare outputs
- [ ] Build a complete system prompt for a "SOC Tier 1 AI Assistant"
- [ ] Practice few-shot prompting for malware IOC extraction
- [ ] Test temperature 0, 0.5, and 1.0 on the same prompt — document differences
- [ ] Create a prompt that generates a threat model for a web application
