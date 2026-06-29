# Day 59 - Lab: OSINT

## Objective
Practice OSINT techniques on a domain you're authorized to research (your own, or explicitly public bug bounty in-scope domains - never random third parties).

## Task 1: Google Dorking Practice
Run these against your own GitHub/website/domain (replace with your own):
```
site:github.com "yourusername" filetype:env
site:yourdomain.com filetype:pdf
```

## Task 2: WHOIS and DNS Recon
```bash
whois yourdomain.com
dig yourdomain.com ANY
nslookup -type=MX yourdomain.com
```

## Task 3: Install and Run theHarvester
```bash
sudo apt install theharvester -y
theHarvester -d yourdomain.com -b google,bing
```

## Task 4: Document Your Own Digital Footprint
Summarize what public information exists about your own domain/accounts - useful both as OSINT practice and personal security awareness.

## Results
| Item | Value |
|---|---|
| Google Dorks run | |
| WHOIS data reviewed (Y/N) | |
| theHarvester results found | |
| Footprint summary written (Y/N) | |

## Lab Summary
Note anything surprising found about your own public digital footprint.
