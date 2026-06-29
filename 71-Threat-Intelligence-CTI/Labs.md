# Day 71 - Lab: Threat Intelligence (CTI)

## Objective
Use open-source threat intelligence to enrich findings from previous lab work.

## Task 1: Check IPs from Your Brute Force Logs in AbuseIPDB
Visit abuseipdb.com and look up the attacking IPs from your Topic 67 sample auth.log:
- 45.33.32.156 (this is actually a well-known scanner, scanme.nmap.org)
- 198.51.100.1

## Task 2: Search a File Hash in VirusTotal
Download the EICAR test file (safe, not real malware):
```bash
echo 'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*' > eicar.txt
md5sum eicar.txt
```
Look up the hash on virustotal.com.

## Task 3: Explore AlienVault OTX
Visit otx.alienvault.com, search for a known malicious domain or IP, and read the associated threat intelligence report.

## Task 4: Enrich Your Pentest Report (from Topic 61)
Add a CTI section to your pentest report documenting any external threat intelligence context for the vulnerabilities found.

## Results
| Item | Value |
|---|---|
| IPs checked in AbuseIPDB (Y/N) | |
| EICAR hash found on VirusTotal (Y/N) | |
| OTX pulse reviewed (Y/N) | |
| CTI enrichment added to pentest report (Y/N) | |

## Lab Summary
Note how quickly AbuseIPDB confirmed 45.33.32.156 as a known scanner, demonstrating the speed value of threat intel lookups.
