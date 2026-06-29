# 86 - AI Security Fundamentals - Labs

## Lab 1: AI System Security Audit
Review an LLM chatbot deployment against this checklist:
- [ ] API authentication (API key / OAuth) configured?
- [ ] Rate limiting enabled?
- [ ] All inputs and outputs logged with timestamps?
- [ ] PII masked before logging?
- [ ] Output filtering for harmful content?
- [ ] Model weights stored encrypted?
- [ ] Prompt injection tested?
- [ ] GDPR/data deletion workflow defined?
- [ ] Incident response plan for model compromise?
- [ ] ML dependency scanning in CI/CD pipeline?

Write a 1-page AI Security Assessment report.

## Lab 2: PII Detection in LLM Outputs
```python
import re

output = "Patient John Smith (DOB: 1985-03-12, SSN: 123-45-6789) at john@hospital.com called 555-234-5678"

patterns = {
    "SSN":   r"\d{3}-\d{2}-\d{4}",
    "Email": r"[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}",
    "Phone": r"\d{3}-\d{3}-\d{4}",
    "DOB":   r"\d{4}-\d{2}-\d{2}",
}
for label, pat in patterns.items():
    hits = re.findall(pat, output)
    print(f"{'[FOUND]' if hits else '[CLEAN]'} {label}: {hits}")
```

## Lab 3: MITRE ATLAS Mapping
Visit atlas.mitre.org and map these 5 threats to ATLAS technique IDs:
1. Training data poisoning
2. Model evasion at inference
3. Model API extraction
4. Prompt injection
5. Membership inference attack

| Threat | ATLAS Tactic | Technique ID | Description |
|--------|-------------|-------------|-------------|

## Practice Challenges
- [ ] Read NIST AI RMF summary — list 5 key risk categories
- [ ] Classify 5 AI apps by EU AI Act risk tier (Minimal/Limited/High/Unacceptable)
- [ ] Write a 1-page AI Security Policy for a fictional company
- [ ] Install Garak (pip install garak) and run a basic LLM scan
- [ ] Research the Samsung ChatGPT data leak (2023) — what went wrong?
