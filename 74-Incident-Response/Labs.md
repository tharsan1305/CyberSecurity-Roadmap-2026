# 74 - Incident Response - Labs

## Lab 1: Phishing Incident Full IR Drill

### Scenario
A user emails the SOC: "I got a weird email from IT asking me to verify my Microsoft login. I clicked the link and entered my password. Was this real?"

### Your Task: Run the Full IR Lifecycle

**Step 1 – Identification**
- Collect the email from the user (or use a sample phishing email)
- Analyze headers using [MXToolbox](https://mxtoolbox.com/EmailHeaders.aspx)
- Check link using [VirusTotal](https://virustotal.com) and [URLScan.io](https://urlscan.io)
- Document: Is this a credential-harvesting phish? Confirmed TP.

**Step 2 – Containment**
- Action: Reset user's Microsoft 365 password immediately
- Action: Enable/enforce MFA on the account
- Action: Block the sender domain in email gateway
- Action: Search all mailboxes for same email (use Exchange admin center or M365 Defender)

**Step 3 – Eradication**
- Scan the user's endpoint with Windows Defender / EDR
- Check sign-in logs in Azure AD for anomalous login from new location
- Revoke all active sessions for the compromised account

**Step 4 – Recovery**
- User logs in with new password + MFA
- Monitor account for 48 hours for suspicious activity

**Step 5 – Report**
Write the full IR report using this template:
```
Incident ID       :
Date Reported     :
Incident Type     : Phishing / Credential Theft
Affected Accounts :
IOCs              : (URL, sender domain)
Timeline          :
  - [time] User clicked link
  - [time] SOC notified
  - [time] Containment completed
Root Cause        :
Impact            :
Actions Taken     :
Lessons Learned   :
```

---

## Lab 2: Ransomware IR Simulation

### Scenario
At 3:15 AM, EDR fires alert: mass file rename activity detected on FILE-SERVER-01. Extensions changed to `.locked`. SMB traffic to 14 endpoints detected.

### Steps
1. **Identify**: Confirm ransomware — check process tree in EDR
2. **Contain**: Network isolate FILE-SERVER-01 immediately. Block SMB laterally.
3. **Assess scope**: Which other systems are affected?
4. **Evidence**: Collect ransom note, encrypted file samples, EDR logs
5. **Eradicate**: Identify ransomware family (use hash on VirusTotal)
6. **Recover**: Restore from last clean backup. Verify backup integrity first.
7. **Report**: Full ransomware IR report

---

## Lab 3: Build a Ransomware Playbook

Create a complete playbook document with these sections:
1. Detection Criteria (what alerts trigger this?)
2. Initial Triage Questions (5 questions to answer in first 15 mins)
3. Containment Procedures (step-by-step)
4. Evidence Collection Checklist
5. Communication Tree (who to notify, in what order)
6. Recovery Procedures
7. Post-Incident Review Template

---

## Practice Challenges
- [ ] Complete TryHackMe "Incident Response" room
- [ ] Download and analyze a public IR report from Mandiant or CrowdStrike
- [ ] Set up TheHive and log a practice incident end-to-end
- [ ] Write a DDoS IR playbook
- [ ] Practice timeline reconstruction from a set of sample logs
