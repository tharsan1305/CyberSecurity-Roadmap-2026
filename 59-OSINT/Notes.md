# Day 59 - OSINT

## Goal
Learn Open Source Intelligence gathering - the reconnaissance foundation for both pentesting and threat intelligence work later.

## 1. Search Engine Techniques (Google Dorking)
Using advanced search operators to find specific, often sensitive, publicly indexed information.
```
site:example.com filetype:pdf          (find PDFs on a specific site)
intitle:"index of" "backup"              (find exposed directory listings)
site:example.com inurl:admin               (find admin login pages)
```

## 2. Social Media Reconnaissance
Gathering publicly available information from LinkedIn, Twitter/X, etc. - often used in social engineering/phishing pretext research (and equally important for understanding your own organization's public exposure).

## 3. WHOIS & DNS Recon
```bash
whois example.com
dig example.com ANY
nslookup -type=MX example.com
```
Reveals domain registration info, mail servers, and DNS infrastructure - useful for mapping an organization's external footprint.

## 4. OSINT Tools (Maltego, theHarvester)
- **theHarvester**: gathers emails, subdomains, names from public sources
- **Maltego**: visual link-analysis tool connecting people, domains, infrastructure

```bash
theHarvester -d example.com -b google
```

## Interview Questions
**Q1. What is a Google Dork?**
An advanced search query using operators (site:, filetype:, intitle:, etc.) to find specific, often unintentionally exposed, information.
**Q2. Why is OSINT a legal/ethical activity even though it's reconnaissance?**
It only uses publicly available information - no unauthorized access occurs, distinguishing it clearly from active hacking.
**Q3. What does theHarvester gather?**
Emails, subdomains, and names associated with a target domain from public sources.

## Key Takeaways
- Learned Google Dorking techniques
- Learned WHOIS/DNS reconnaissance
- Learned theHarvester and Maltego use cases
