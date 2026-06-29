# 75 - Security Operations - Labs

## Lab 1: Create a SecOps Daily Runbook

### Objective
Build a complete daily operational runbook for a mock SOC.

### Sections to Create
1. Pre-shift startup checklist (verify tools, review overnight queue)
2. Alert handling procedure (step-by-step from alert to close/escalate)
3. Shift handover template
4. Tool health check procedure
5. End-of-shift report template

---

## Lab 2: Build a SOC Metrics Dashboard

### Objective
Create an automated metrics tracker in Google Sheets or Excel.

### Setup Steps
1. Create a spreadsheet with daily log columns:
   `Date | Analyst | Total Alerts | TP | FP | Escalations | MTTD | MTTR`
2. Add calculated columns:
   - TP Rate = TP/Total × 100
   - FP Rate = FP/Total × 100
3. Add 2 weeks of simulated data
4. Create charts:
   - Daily Alert Volume (line chart)
   - TP vs FP per day (stacked bar)
   - MTTD Trend over 2 weeks (line chart)
5. Add conditional formatting: Red if FP Rate > 40%, Green if < 20%

---

## Lab 3: SOAR Automation Simulation

### Objective
Simulate a SOAR automation workflow for phishing alert response.

### Manual vs Automated Comparison
| Task                         | Manual Time | Automated (SOAR) |
|------------------------------|-------------|------------------|
| Check URL in VirusTotal      | 3 min       | < 10 seconds     |
| Search email across mailboxes| 15 min      | < 1 minute       |
| Reset user password          | 5 min       | Automatic        |
| Create ticket with evidence  | 10 min      | Automatic        |
| Total                        | 33 min      | ~2 minutes       |

### Steps
1. Document the manual phishing response workflow (draw flowchart)
2. Identify automation opportunities at each step
3. Write pseudo-code for an automated playbook:
```
TRIGGER: Phishing email alert from email gateway

ACTION 1: Extract URL from email body
ACTION 2: Submit URL to VirusTotal API → get verdict
ACTION 3: IF malicious → block URL at proxy
ACTION 4: Search mailboxes for same email → delete all copies
ACTION 5: Check if user clicked → IF yes, reset password
ACTION 6: Create incident ticket with all evidence attached
ACTION 7: Notify SOC analyst via Slack
```
4. (Optional) Implement in n8n (free SOAR-like tool)

---

## Practice Challenges
- [ ] Write a full shift handover document for a simulated 8-hour SOC shift
- [ ] Build a weekly SOC report from sample data
- [ ] Research and compare 3 SOAR platforms (Splunk SOAR, XSOAR, Shuffle)
- [ ] Set up Shuffle (free open-source SOAR) and create a basic automation
- [ ] Document the tool stack you would choose for a 50-person company SOC
