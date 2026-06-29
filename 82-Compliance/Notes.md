# 82 - Compliance (ISO 27001, NIST, PCI-DSS)

## Overview
Compliance refers to adhering to laws, regulations, frameworks, and standards that govern how organizations must protect information. Non-compliance can result in fines, legal action, and reputational damage.

---

## 1. ISO 27001 – ISMS Standards

### What is ISO 27001?
International standard for establishing, implementing, maintaining, and improving an Information Security Management System (ISMS).

### Key Concepts
- **ISMS**: Information Security Management System — the overall framework
- **Statement of Applicability (SoA)**: Documents which Annex A controls apply and why
- **Annex A**: 93 security controls grouped into 4 categories

### ISO 27001 Annex A Control Categories
| Category       | Controls | Examples                              |
|----------------|----------|---------------------------------------|
| Organizational | 37       | Info security policies, roles, supplier security |
| People         | 8        | Screening, training, disciplinary process |
| Physical       | 14       | Physical access, equipment protection |
| Technological  | 34       | Access control, cryptography, network security |

### Certification Process
1. Gap assessment vs ISO 27001 requirements
2. Implement required controls
3. Internal audit
4. Stage 1 audit (documentation review)
5. Stage 2 audit (on-site assessment)
6. Certification issued (valid 3 years)
7. Annual surveillance audits

---

## 2. NIST Cybersecurity Framework (CSF)

### CSF 2.0 Core (6 Functions)
| Function  | Description                                          |
|-----------|------------------------------------------------------|
| Govern    | Cybersecurity strategy, policy, roles, risk management |
| Identify  | Asset management, risk assessment, supply chain      |
| Protect   | Access control, training, data security, resilience  |
| Detect    | Monitoring, anomaly detection, event analysis        |
| Respond   | IR planning, communications, analysis, mitigation    |
| Recover   | Recovery planning, improvements, communications      |

### Implementation Tiers
- **Tier 1 – Partial**: Ad hoc, reactive
- **Tier 2 – Risk Informed**: Risk-aware but not org-wide
- **Tier 3 – Repeatable**: Formal policies and procedures
- **Tier 4 – Adaptive**: Continuously improving, threat-aware

---

## 3. PCI-DSS – Payment Card Security

### What is PCI-DSS?
Payment Card Industry Data Security Standard — mandatory for any organization that processes, stores, or transmits cardholder data (credit/debit card info).

### PCI-DSS v4.0 – 12 Requirements
| # | Requirement                                              |
|---|----------------------------------------------------------|
| 1 | Install and maintain network security controls (firewalls) |
| 2 | Apply secure configurations to all system components      |
| 3 | Protect stored account data (encryption, masking)         |
| 4 | Protect cardholder data in transit with strong cryptography|
| 5 | Protect systems from malicious software                   |
| 6 | Develop and maintain secure systems (patch management)    |
| 7 | Restrict access to system components by business need     |
| 8 | Identify users and authenticate access (MFA required)     |
| 9 | Restrict physical access to cardholder data               |
| 10| Log and monitor all access to system components           |
| 11| Test security systems and processes regularly             |
| 12| Support info security with organizational policies        |

### Compliance Levels
| Level | Annual Transactions | Assessment Method            |
|-------|---------------------|------------------------------|
| 1     | > 6 million         | Annual on-site QSA audit     |
| 2     | 1-6 million         | Annual SAQ + quarterly scans |
| 3     | 20,000 - 1 million  | Annual SAQ + quarterly scans |
| 4     | < 20,000            | Annual SAQ                   |

---

## 4. Audit & Certification Process

### Types of Audits
| Type            | Description                                          |
|-----------------|------------------------------------------------------|
| Internal Audit  | Conducted by organization's own team                 |
| External Audit  | Independent third-party audit                        |
| Gap Assessment  | Identify gaps before formal audit                    |
| Penetration Test| Required by PCI-DSS, ISO 27001 best practice         |

### Common Audit Evidence Types
- Policies and procedures (documented)
- System configuration screenshots
- Access control lists and user reviews
- Patch management records
- Security training completion records
- Incident response logs
- Vulnerability scan reports
