# 80 - Risk Management - Labs

## Lab 1: Risk Assessment for a Fictional Company

### Scenario
TechCorp (100 employees) stores customer PII in an on-premises database. No MFA, basic antivirus, no security monitoring.

### Your Task
Complete a risk assessment:

1. **Identify 10 risks** (e.g., ransomware, phishing, insider threat, SQL injection, etc.)
2. **Score each risk**: Likelihood (1-5) × Impact (1-5) = Risk Score (1-25)
3. **Categorize**: 1-5 = Low, 6-12 = Medium, 13-19 = High, 20-25 = Critical
4. **Select treatment**: Mitigate / Accept / Transfer / Avoid
5. **Identify control**: What specific control addresses each risk?

| Risk ID | Risk | Likelihood | Impact | Score | Category | Treatment | Control |
|---------|------|------------|--------|-------|----------|-----------|---------|

---

## Lab 2: Build a Risk Register

### Steps
1. Using the risk assessment from Lab 1, build a full Risk Register in Excel/Sheets
2. Add columns: Risk Owner, Due Date, Status, Residual Risk (after control)
3. Sort by Risk Score (highest first)
4. Add conditional formatting: Critical = Red, High = Orange, Medium = Yellow
5. Add a summary dashboard showing: Total risks, by category, by status

---

## Lab 3: Quantitative Risk Calculation (ALE)

### Scenario
Asset: Customer database (value = $500,000)
Threat: SQL injection attack
Exposure Factor: 40% (40% of database compromised per incident)
ARO: 0.5 (happens once every 2 years)

### Calculate
```
SLE = Asset Value × Exposure Factor
    = $500,000 × 0.40
    = $200,000

ALE = SLE × ARO
    = $200,000 × 0.5
    = $100,000 per year

Control Cost: WAF costs $8,000/year and reduces ARO to 0.1

New ALE = $200,000 × 0.1 = $20,000
Risk Reduction Value = $100,000 - $20,000 = $80,000/year
Net Benefit of WAF = $80,000 - $8,000 = $72,000/year
```

### Practice
Calculate ALE for 3 different risk scenarios using your own numbers.

---

## Practice Challenges
- [ ] Complete a full risk assessment for your home network
- [ ] Research NIST SP 800-30 (Risk Assessment Guide) and summarize key steps
- [ ] Build a risk register in Excel with 15+ risks and full treatment plans
- [ ] Calculate ALE for 5 different scenarios with different asset values
- [ ] Research and compare NIST RMF vs ISO 31000 — write a 1-page comparison
