# Day 72 - Lab: MITRE ATT&CK Framework

## Objective
Use the ATT&CK Navigator to map your lab pentesting activities and plan detection coverage.

## Task 1: Explore ATT&CK Navigator
Visit mitre-attack.github.io/attack-navigator
Create a new layer, search for techniques you've practiced:
- T1566 (Phishing)
- T1110 (Brute Force)
- T1558.003 (Kerberoasting)
- T1078 (Valid Accounts)

Color them (e.g., red = tested, blue = detected).

## Task 2: Map Your Lab Activities
For your Metasploitable2 pentest from Topic 61, identify and document the ATT&CK techniques you used at each phase.

## Task 3: Identify Detection Gaps
For each technique you marked as "tested" in the Navigator, check if your Wazuh/SIEM setup from Topics 68-69 would actually detect it. Mark undetected techniques as coverage gaps.

## Task 4: Run an Atomic Red Team Test (Optional)
```bash
# Install Atomic Red Team (PowerShell, Windows)
IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1')
Invoke-AtomicTest T1110 -TestNumbers 1
```

## Results
| Item | Value |
|---|---|
| ATT&CK Navigator layer created (Y/N) | |
| Lab activities mapped to ATT&CK IDs (Y/N) | |
| Detection gaps identified | |
| Atomic test run (Y/N) | |

## Lab Summary
Note how many of your lab pentest techniques would have been detected by your current Wazuh setup versus how many would have been missed.
