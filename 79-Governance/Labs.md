# 79 - Governance - Labs

## Lab 1: Write an Acceptable Use Policy

### Objective
Draft a realistic AUP for a fictional company.

### Template Sections
```
ACCEPTABLE USE POLICY
Company: [Name]
Version: 1.0
Effective Date:
Approved By:

1. PURPOSE
   This policy defines acceptable use of [Company]'s IT resources...

2. SCOPE
   Applies to all employees, contractors, and third parties...

3. ACCEPTABLE USE
   - Systems may be used for legitimate business purposes only
   - Limited personal use is permitted provided it does not...

4. PROHIBITED ACTIVITIES
   - Accessing unauthorized systems or data
   - Installing unauthorized software
   - Sharing login credentials
   - Visiting inappropriate websites
   - Using company systems for personal business ventures

5. SOCIAL MEDIA
   - Do not share confidential company information publicly
   - Do not post about security incidents or internal matters

6. ENFORCEMENT
   Violations may result in disciplinary action up to and including termination...

7. REVIEW
   This policy will be reviewed annually.
```

---

## Lab 2: NIST CSF Gap Assessment

### Objective
Perform a basic gap assessment against the NIST CSF for a fictional organization.

### Scenario
A 200-person company has: basic firewall, no SIEM, no formal IR plan, ad-hoc patching, no security training program.

### Assessment Table
| CSF Function | Control Area          | Current State | Target State | Gap |
|--------------|-----------------------|---------------|--------------|-----|
| Identify     | Asset inventory       | Partial       | Complete     | Medium |
| Protect      | Access control        | Basic (no MFA)| MFA enforced | High |
| Protect      | Security training     | None          | Annual training| Critical |
| Detect       | SIEM monitoring       | None          | 24/7 SIEM   | Critical |
| Respond      | IR Plan               | None          | Documented plan| Critical |
| Recover      | Backup & recovery     | Partial       | Tested weekly| High |

### Steps
1. Fill in the table for all 5 CSF functions
2. Prioritize the top 5 gaps by risk
3. Write a 1-paragraph recommendation for each top gap
4. Estimate cost and effort for each remediation

---

## Lab 3: Build a Security Awareness Program Plan

### Plan Sections
1. **Goals**: Reduce phishing click rate to < 5%
2. **Audience**: All 200 employees
3. **Delivery Method**: LMS (KnowBe4/free alternative: Security Awareness Company)
4. **Training Schedule**: Onboarding + Annual + Monthly tips
5. **Phishing Simulations**: Quarterly campaigns
6. **Metrics**: Click rate, reporting rate, completion rate
7. **Reporting**: Monthly dashboard to management

---

## Practice Challenges
- [ ] Draft a complete Password Policy for a fictional company
- [ ] Map 10 security controls to the NIST CSF framework
- [ ] Research ISO 27001 Annex A controls and summarize 5 key control categories
- [ ] Build a data classification scheme with 4 tiers and handling rules for each
- [ ] Create a 1-page RACI chart for a security team of 6 people
