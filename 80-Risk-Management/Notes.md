# 80 - Risk Management

## Overview
Risk Management is the ongoing process of identifying, assessing, and responding to risks that could impact an organization's information assets and business objectives.

---

## 1. Risk Identification & Assessment

### Key Risk Concepts
| Term            | Definition                                                  |
|-----------------|-------------------------------------------------------------|
| Asset           | Anything of value (data, systems, people)                   |
| Threat          | Anything that could cause harm (hacker, fire, employee)     |
| Vulnerability   | Weakness that a threat can exploit                          |
| Risk            | Probability of threat exploiting vulnerability × Impact     |
| Control         | Measure to reduce risk                                      |
| Residual Risk   | Risk remaining after controls are applied                   |

### Risk Formula
```
Risk = Likelihood × Impact

Qualitative  : Low/Medium/High/Critical
Quantitative : Annual Loss Expectancy (ALE) = ARO × SLE
  - ARO = Annualized Rate of Occurrence (how often/year)
  - SLE = Single Loss Expectancy ($) = Asset Value × Exposure Factor
```

### Risk Assessment Methods
- **Qualitative**: Uses scales (Low/Med/High), subjective judgment
- **Quantitative**: Uses dollar values, statistical data, ALE calculations
- **Semi-Quantitative**: Numeric scales (1-5) without true dollar values

### Risk Matrix
```
         | Low Impact | Med Impact | High Impact |
---------|------------|------------|-------------|
High Prob|   Medium   |    High    |  Critical   |
Med Prob |    Low     |   Medium   |    High     |
Low Prob |    Low     |    Low     |   Medium    |
```

---

## 2. Risk Treatment Options

| Option    | Description                                         | Example                    |
|-----------|-----------------------------------------------------|----------------------------|
| Mitigate  | Reduce likelihood or impact with controls           | Install firewall, patch OS |
| Accept    | Knowingly accept the risk (low risk or high cost)   | Accept low-value asset risk|
| Transfer  | Shift risk to third party                           | Cyber insurance, outsource |
| Avoid     | Stop the activity that creates the risk             | Don't store PII at all     |

---

## 3. Risk Register

### What is a Risk Register?
A documented inventory of all identified risks, their ratings, owners, and treatment plans.

### Risk Register Template
| Risk ID | Risk Description | Asset | Threat | Vulnerability | Likelihood | Impact | Risk Score | Treatment | Owner | Due Date | Status |
|---------|-----------------|-------|--------|---------------|------------|--------|------------|-----------|-------|----------|--------|
| R001    | Ransomware attack on file server | File Server | Ransomware | No EDR, no backup | High | Critical | Critical | Mitigate: Deploy EDR + offline backups | IT Manager | 30 days | Open |

---

## 4. Frameworks – NIST RMF & ISO 31000

### NIST Risk Management Framework (RMF) – 7 Steps
1. **Prepare** – Establish context and strategy
2. **Categorize** – Classify system based on data sensitivity
3. **Select** – Choose appropriate security controls (NIST 800-53)
4. **Implement** – Deploy the selected controls
5. **Assess** – Test controls for effectiveness
6. **Authorize** – Formally accept residual risk (ATO decision)
7. **Monitor** – Continuously monitor controls and risks

### ISO 31000 – Risk Management Principles
- Integrated into organizational processes
- Structured and comprehensive
- Customized to context
- Inclusive of all stakeholders
- Dynamic and iterative
- Best available information
- Human and cultural factors considered
- Continual improvement
