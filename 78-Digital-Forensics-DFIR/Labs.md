# 78 - Digital Forensics (DFIR) - Labs

## Lab 1: Disk Image Analysis with Autopsy

### Objective
Analyze a forensic disk image to find evidence of unauthorized activity.

### Practice Images (Free)
- [Digital Corpora](https://digitalcorpora.org/) – Real forensic case images
- [CFReDS (NIST)](https://www.cfreds.nist.gov/) – Forensic reference datasets
- [CTF Forensics challenges](https://ctftime.org/)

### Steps
1. Download Autopsy (free): [autopsy.com](https://www.autopsy.com/)
2. Download a sample disk image (e.g., from Digital Corpora)
3. Create new Autopsy case → Add disk image as data source
4. Enable all ingest modules and wait for analysis
5. Investigate:
   - What user accounts exist?
   - What programs were recently executed? (Check Prefetch)
   - Any deleted files recovered?
   - Browser history — what sites were visited?
   - Any external drives connected? (USB history)
6. Build a timeline of events and document findings

---

## Lab 2: Memory Forensics with Volatility

### Objective
Analyze a memory dump to identify malware or suspicious processes.

### Practice Memory Dumps
- [MemLabs (GitHub)](https://github.com/stuxnet999/MemLabs) – CTF-style memory forensics
- Any.run sandbox can download memory dumps of running malware

### Setup
```bash
# Install Volatility 3
git clone https://github.com/volatilityfoundation/volatility3.git
cd volatility3
pip install -r requirements.txt
```

### Analysis Steps
```bash
# Step 1: Identify OS profile
python vol.py -f memory.dmp windows.info

# Step 2: List all processes
python vol.py -f memory.dmp windows.pslist > processes.txt

# Step 3: Look for suspicious processes
# Red flags: cmd.exe with no parent, svchost not from services.exe,
# browsers making network connections to unusual IPs

# Step 4: Check network connections
python vol.py -f memory.dmp windows.netstat

# Step 5: Look for injected code
python vol.py -f memory.dmp windows.malfind
```

### Document Your Findings
```
Memory Dump    :
OS Version     :
Suspicious Process:
  PID          :
  Parent PID   :
  Reason suspicious:
Network Connections:
Injected Code Found? :
```

---

## Lab 3: Build a Forensic Investigation Report

### Scenario
You are handed a disk image from a company laptop suspected of data exfiltration.

### Questions to Answer
1. What user was logged in?
2. What files were accessed in the last 7 days?
3. Was any sensitive data copied to external media?
4. Were any unauthorized programs installed?
5. Any evidence of data exfiltration (cloud uploads, email attachments)?

### Report Template
```
FORENSIC INVESTIGATION REPORT

Case ID          :
Investigator     :
Date             :
Evidence Item    :
Hash (SHA256)    :

EXECUTIVE SUMMARY
[2-3 line summary]

FINDINGS
1. [Finding + supporting evidence + timestamp]
2. [Finding + supporting evidence + timestamp]

TIMELINE
[Chronological events with timestamps]

CONCLUSION
[Was data exfiltrated? What happened?]

EVIDENCE LIST
[All items collected with hashes]
```

---

## Practice Challenges
- [ ] Complete all 6 MemLabs challenges on GitHub
- [ ] Analyze a disk image from Digital Corpora and write a full forensic report
- [ ] Complete TryHackMe "Digital Forensics" or "DFIR" rooms
- [ ] Capture RAM from your own Windows VM and run Volatility analysis
- [ ] Research and document Windows forensic artifacts: Prefetch, LNK, Shellbags
