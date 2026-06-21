# Day 16 - Lab: Regex Practice

## Objective
Build practical regex patterns to parse a sample log file and validate input.

## Setup - Create a Sample Log
```bash
cat << 'EOF' > sample_access.log
192.168.1.10 - - [21/Jun/2026:10:00:01] "GET /login HTTP/1.1" 200
192.168.1.55 - - [21/Jun/2026:10:01:15] "POST /login HTTP/1.1" 401
10.0.0.5 - - [21/Jun/2026:10:02:00] "GET /admin?id=1' OR '1'='1 HTTP/1.1" 403
192.168.1.10 - - [21/Jun/2026:10:03:45] "GET /dashboard HTTP/1.1" 200
EOF
```

## Task 1: Extract All IP Addresses
```python
import re

with open("sample_access.log") as f:
    content = f.read()

ips = re.findall(r'\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b', content)
print("IPs found:", ips)
```

## Task 2: Extract All HTTP Status Codes
```python
status_codes = re.findall(r'"\s(\d{3})$', content, re.MULTILINE)
print("Status codes:", status_codes)
```

## Task 3: Detect Suspicious SQLi-Like Patterns
```python
sqli_pattern = r"(\bOR\b\s+'?\d+'?=\s*'?\d+'?|\bUNION\b|--)"
for line in content.splitlines():
    if re.search(sqli_pattern, line, re.IGNORECASE):
        print("SUSPICIOUS LINE:", line)
```

## Task 4: Validate a List of Emails
```python
emails = ["good@example.com", "bad-email", "another@test.org", "missing@domain"]
email_pattern = r'^[\w\.-]+@[\w\.-]+\.\w+$'

for email in emails:
    valid = bool(re.match(email_pattern, email))
    print(f"{email}: {'Valid' if valid else 'Invalid'}")
```

## Results
| Item | Value |
|---|---|
| IPs extracted | |
| Status codes found | |
| Suspicious lines detected | |
| Valid emails count | |

## Screenshots
```
![IP Extraction](Screenshots/ip-extraction.png)
![SQLi Detection](Screenshots/sqli-detection.png)
```

## Lab Summary
Note how confident you feel writing regex from scratch now versus before today, and which pattern type (quantifiers, groups, lookarounds) still feels unclear.
