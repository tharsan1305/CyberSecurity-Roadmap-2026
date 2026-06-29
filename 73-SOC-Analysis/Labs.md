# 73 - SOC Analysis - Labs

## Lab 1: Build a Home SOC Lab

### Objective
Set up a functional SOC environment to practice detection and alert triage.

### Tools Needed
- VirtualBox (free) + Ubuntu Server VM + Windows 10 VM
- Wazuh (free open-source SIEM + EDR) OR Elastic SIEM

### Steps
1. Install VirtualBox and create Ubuntu Server + Windows 10 VMs
2. Install Wazuh Manager on Ubuntu: `curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && bash wazuh-install.sh -a`
3. Install Wazuh Agent on Windows 10 endpoint
4. Log into Wazuh dashboard at https://localhost
5. Navigate to Security Events and observe real-time logs
6. Simulate a brute-force login on Windows with bad passwords
7. Observe Event ID 4625 alerts appear in Wazuh dashboard

### Expected Result
- Failed login alerts visible in SIEM
- Ability to filter by Event ID, user, and source IP

---

## Lab 2: Alert Triage Practice with Sample Logs

### Objective
Practice triaging realistic alerts using public security datasets.

### Dataset Source
Download from: https://github.com/splunk/attack_data or https://github.com/OTRF/Security-Datasets

### Steps
1. Import logs into Splunk Free or Elastic
2. Find the following event types and classify each:
   - Event ID 4625 – Failed login
   - Event ID 4720 – New account created
   - Event ID 4672 – Special privileges assigned
   - Event ID 4104 – PowerShell script block logging
3. For each alert, complete a triage form:

```
Alert ID      :
Timestamp     :
Source IP     :
Target System :
Event Type    :
Severity      : Critical / High / Medium / Low
FP or TP      :
Evidence      :
Action Taken  :
```

---

## Lab 3: Write Custom SIEM Detection Rules

### Scenario A – Credential Stuffing Detection (Splunk SPL)
```spl
index=windows (EventCode=4625 OR EventCode=4624)
| stats count(eval(EventCode=4625)) as failed,
        count(eval(EventCode=4624)) as success
  by src_ip, user
| where failed > 5 AND success >= 1
| table src_ip, user, failed, success
```

### Scenario B – New Admin Account Created After Hours (Splunk)
```spl
index=windows EventCode=4720
| eval hour=strftime(_time, "%H")
| where hour < 8 OR hour > 18
| table _time, user, src_ip
```

### Steps
1. Load sample Windows Security logs into Splunk
2. Run each query and observe results
3. Save as an Alert with a 15-minute trigger interval
4. Document: What does this rule detect? What are the false positive conditions?

---

## Lab 4: SOC Metrics Dashboard

### Objective
Build a daily SOC metrics tracker spreadsheet.

### Columns
| Date | Analyst | Total Alerts | True Positives | False Positives | Escalations | MTTD (min) | MTTR (min) |

### Steps
1. Create the spreadsheet
2. Add 5 days of simulated data
3. Add formula: `FP Rate = FP / Total Alerts * 100`
4. Create bar charts: TP vs FP per day, MTTD trend over week
5. Write a 5-line analyst performance summary

---

## Practice Challenges
- [ ] Complete TryHackMe "SOC Level 1" learning path (free)
- [ ] Triage 20 alerts from Boss of the SOC (BOTS) dataset
- [ ] Write SPL query to detect PowerShell download cradle
- [ ] Set up LetsDefend free account and complete 3 alert investigations
- [ ] Write a 1-page SOC Analyst daily runbook for your home lab
