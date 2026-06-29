# 85 - Prompt Engineering

## Overview
Prompt Engineering is the practice of crafting effective inputs to AI language models to reliably achieve desired outputs. It is a critical skill for anyone working with LLMs.

---

## 1. Prompt Structure & Techniques

### Anatomy of an Effective Prompt
```
[ROLE]       → "You are a senior cybersecurity analyst..."
[CONTEXT]    → "We have detected suspicious PowerShell activity..."
[TASK]       → "Analyze the following log entry and identify..."
[FORMAT]     → "Respond in JSON with fields: severity, ioc_type, recommendation"
[CONSTRAINTS]→ "Be concise. Only include confirmed IOCs."
[EXAMPLES]   → "Here is an example of the expected output..."
```

### Positive vs Negative Instructions
```
WEAK:  "Don't be vague"
STRONG: "Provide specific, actionable steps with commands"

WEAK:  "Summarize this"
STRONG: "Write a 3-bullet summary, each bullet max 20 words, focus on security impact"
```

---

## 2. Few-Shot / Zero-Shot Prompting

### Zero-Shot
No examples — rely on the model's training.
```
Classify this email as PHISHING or LEGITIMATE:
"Urgent: Your account will be suspended. Click here to verify."
```

### One-Shot
One example to guide the model.
```
Email: "Congratulations! You won a prize. Click here."
Classification: PHISHING

Email: "Your invoice #4521 is attached for review."
Classification:
```

### Few-Shot
Multiple examples for complex tasks.
```
Log: "Failed login from 192.168.1.5 for user admin" → Severity: Medium, Type: Brute Force
Log: "Ransomware detected: files encrypted on C:\" → Severity: Critical, Type: Ransomware
Log: "User john downloaded 500MB to USB drive"   → Severity: High, Type: Data Exfil

Log: "New admin account 'svc_backup' created at 3AM" → Severity:
```

---

## 3. Chain-of-Thought Prompting

### What is CoT?
Asking the model to reason step-by-step before giving a final answer. Dramatically improves accuracy on complex reasoning tasks.

### Standard vs CoT
```
STANDARD:
  Q: Is this IP address (203.0.113.5) likely malicious?
  A: No.  [Short, possibly wrong]

CHAIN-OF-THOUGHT:
  Q: Is this IP address (203.0.113.5) likely malicious? Think step by step.
  A: Step 1: 203.0.113.x is a TEST-NET range defined in RFC 5737.
     Step 2: TEST-NET addresses are reserved for documentation only.
     Step 3: Any traffic from this range in production is abnormal.
     Step 4: This could indicate IP spoofing or an attacker using reserved ranges.
     Conclusion: This IP should be investigated — it should not appear in production traffic.
```

### Zero-Shot CoT
Add "Let's think step by step." or "Think step by step:" to any prompt.

---

## 4. Prompt Optimization Techniques

### Techniques
| Technique             | Description                                        |
|-----------------------|----------------------------------------------------|
| System Prompt         | Set persistent role and constraints                |
| Temperature Control   | 0 = deterministic, 1.0 = creative                 |
| XML Tags              | Use `<context>`, `<task>`, `<format>` for clarity  |
| Output Format Control | "Respond ONLY in JSON", "Use markdown table"       |
| Self-Consistency      | Generate multiple CoT responses, take majority vote|
| ReAct                 | Reason + Act: interleave reasoning and tool use    |

### Security Analyst System Prompt Template
```
You are an expert cybersecurity analyst with 15 years of experience in SOC operations,
incident response, and threat intelligence. 

When analyzing security data:
- Always identify the MITRE ATT&CK tactic and technique if applicable
- Rate severity as: Critical / High / Medium / Low
- Provide specific, actionable recommendations
- If you are uncertain, say so — never fabricate IOCs or conclusions
- Format your response as: [Severity] | [Summary] | [MITRE Technique] | [Action]
```
