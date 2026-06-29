# 82 - Compliance - Labs

## Lab 1: ISO 27001 Gap Assessment

### Scenario
A financial services company wants to achieve ISO 27001 certification. You are the GRC analyst performing the gap assessment.

### Steps
1. Download the free ISO 27001 controls checklist (search "ISO 27001 Annex A checklist Excel free")
2. For each control category, assess: Not Implemented / Partial / Fully Implemented
3. Calculate: compliance percentage per category
4. Identify top 10 gaps
5. Prioritize by risk (Critical/High/Medium)
6. Write a remediation roadmap with realistic timelines

### Sample Output
| Control | Description | Status | Gap | Priority | Remediation |
|---------|-------------|--------|-----|----------|-------------|
| A.5.1   | Info security policies | Partial | Policy not reviewed in 2 years | Medium | Review and update policy Q1 |
| A.8.3   | Info access restriction | Not implemented | No role-based access control | High | Implement RBAC in 60 days |

---

## Lab 2: PCI-DSS Self-Assessment Questionnaire (SAQ)

### Objective
Practice completing a PCI-DSS SAQ-A (simplest version for e-commerce merchants).

### Steps
1. Download PCI-DSS SAQ-A from: [pcisecuritystandards.org](https://www.pcisecuritystandards.org/document_library/)
2. For each question, answer: Yes / No / N/A
3. For any "No" answers, document:
   - What remediation is required?
   - Who is responsible?
   - By when?
4. Produce a 1-page summary of current PCI-DSS compliance status

---

## Lab 3: Build a Compliance Dashboard

### Objective
Build a compliance tracking dashboard in Excel or Google Sheets.

### Sections
1. **Framework**: ISO 27001 / PCI-DSS / NIST CSF
2. **Control ID and Description**
3. **Compliance Status**: Compliant / Partial / Non-Compliant / N/A
4. **Evidence**: What evidence exists?
5. **Owner**: Who is responsible?
6. **Due Date**: When will gaps be remediated?
7. **Summary metrics**: % Compliant per framework

Add a pie chart showing: Compliant / Partial / Non-Compliant split.

---

## Practice Challenges
- [ ] Research GDPR requirements and map 5 key requirements to ISO 27001 controls
- [ ] Download and review a public ISO 27001 Statement of Applicability template
- [ ] Summarize the difference between PCI-DSS Levels 1, 2, 3, and 4
- [ ] Build a compliance calendar: key dates for audits, reviews, and renewals
- [ ] Research HIPAA Security Rule and identify 5 key requirements
