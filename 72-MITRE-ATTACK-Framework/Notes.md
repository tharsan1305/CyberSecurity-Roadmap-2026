# Day 72 - MITRE ATT&CK Framework

## Goal
Learn MITRE ATT&CK - the most referenced framework in modern security operations, connecting attacks to defensive detection strategies.

## 1. Tactics & Techniques Matrix
ATT&CK organizes adversary behavior into:
- **Tactics**: the "why" - the adversary's goal (e.g., Initial Access, Persistence, Lateral Movement, Exfiltration) - currently 14 Enterprise tactics
- **Techniques**: the "how" - specific methods to achieve a tactic (e.g., T1566.001 - Phishing: Spearphishing Attachment)
- **Sub-techniques**: more specific variations of techniques

Access the full matrix at attack.mitre.org.

## 2. Mapping Attacks to Framework
Every attack you've learned so far maps to ATT&CK:
| Attack | ATT&CK Tactic | Technique |
|---|---|---|
| Phishing email | Initial Access | T1566 |
| Kerberoasting | Credential Access | T1558.003 |
| Pass-the-Hash | Lateral Movement | T1550.002 |
| S3 data exfil | Exfiltration | T1530 |

## 3. Adversary Emulation
Using ATT&CK to design realistic attack simulations - red teams pick a known threat actor's TTPs (e.g., APT29, Lazarus Group) and simulate those specific techniques to test an organization's defenses.

Tools: Atomic Red Team (individual technique tests), CALDERA (automated adversary emulation).

## 4. Detection Engineering
For each ATT&CK technique, the framework lists potential data sources and detection ideas - invaluable for SIEM rule development and SOC detection coverage mapping.

Example: T1110 (Brute Force) -> data sources: Authentication Logs -> detection: spike in failed logins per account/IP (exactly what you built in Topics 67-68).

## Interview Questions
**Q1. What are the three levels of ATT&CK?**
Tactics (the goal), Techniques (the method), Sub-techniques (specific variations).
**Q2. How is ATT&CK useful for detection engineering?**
Each technique lists data sources and detection guidance, enabling SOC teams to map coverage gaps and write targeted SIEM rules.
**Q3. What is adversary emulation, and how does ATT&CK enable it?**
Simulating a specific threat actor's TTPs to test defenses realistically; ATT&CK documents known threat actor TTP mappings, making it the reference for building realistic red team scenarios.

## Key Takeaways
- Learned ATT&CK Tactics, Techniques, and Sub-techniques structure
- Learned to map attacks from earlier topics to ATT&CK IDs
- Learned adversary emulation use cases
- Learned how ATT&CK drives detection engineering in SOC operations
