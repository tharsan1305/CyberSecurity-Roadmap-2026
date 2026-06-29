# 89 - AI Red Teaming
## Overview
AI Red Teaming systematically probes AI systems to find vulnerabilities, unsafe behaviors, and failure modes before they can be exploited in production.

## 1. What to Test
- Prompt injection susceptibility (direct and indirect)
- Jailbreak resistance across multiple techniques
- Harmful content generation (CBRN, violence, illegal)
- PII leakage from training data
- System prompt extraction
- Hallucination rate on factual queries
- Bias across demographic groups
- Consistency under rephrasing

## 2. Attack Simulation Frameworks
| Framework | Description |
|-----------|-------------|
| PyRIT (Microsoft) | Python Risk Identification Toolkit for LLMs |
| Garak | Open-source LLM vulnerability scanner |
| PromptBench | Robustness benchmark for LLMs |
| MITRE ATLAS | Adversarial threat scenarios and case studies |
| HarmBench | Standardized benchmark for LLM safety evaluation |

## 3. Red Team Methodology
### Phase 1: Reconnaissance
- Identify model vendor, version, fine-tuning, and deployment context
- Map all capabilities and tool access (API only? Agent with tools?)
- Identify trust boundaries and sensitive data access

### Phase 2: Threat Modeling
- What harms could this system enable?
- Who are potential adversaries (external attackers, insiders, automated)?
- Map threat scenarios to MITRE ATLAS tactics

### Phase 3: Attack Execution
- Manual: human red teamers craft adversarial prompts
- Automated: Garak probes, PyRIT orchestrators, fuzzing
- Multi-turn: build rapport across conversation turns before attacking
- Edge cases: other languages, encoding tricks, unusual input formats

### Phase 4: Reporting
```
TITLE: [Vulnerability Name]
SEVERITY: Critical / High / Medium / Low
SYSTEM: [Model, version, deployment context]
CATEGORY: [Prompt Injection / Jailbreak / Data Leakage / ...]
OWASP LLM #: [Relevant item]
DESCRIPTION: [What is the vulnerability?]
STEPS TO REPRODUCE:
  1. System prompt: [...]
  2. User input: [...]
  3. Model output: [...]
IMPACT: [What harm could this cause?]
REMEDIATION: [Specific recommended fix]
```

## 4. AI Red Team vs Traditional Red Team
| Aspect | Traditional Red Team | AI Red Team |
|--------|---------------------|-------------|
| Target | Systems, networks, apps | AI models, pipelines, agents |
| Tools | Metasploit, Burp, Nmap | Garak, PyRIT, custom prompts |
| Techniques | Exploits, privilege escalation | Prompt injection, jailbreaks, poisoning |
| Artifacts | Shells, access | Harmful outputs, data leakage |
| Standards | CVE, CVSS | MITRE ATLAS, OWASP LLM |
