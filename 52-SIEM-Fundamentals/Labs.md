# Day 52 - Lab: SIEM Concepts via a Free Platform Preview

## Objective
Get a first hands-on look at a SIEM platform's interface and basic search/correlation concepts, ahead of the deeper Wazuh (Topic 68) and Splunk (Topic 69) labs.

## Task 1: Set Up a Minimal Wazuh Instance (Quick Preview)
```bash
docker run -d --name wazuh-preview -p 443:443 wazuh/wazuh-manager:latest
```
(Full proper Wazuh setup with agents happens in Topic 68 - this is just to see the interface today.)

## Task 2: Generate Sample Log Events to Analyze
Using the sample log generation approach from Topic 16:
```bash
cat << 'EOF' > sample_security.log
2026-06-21 09:00:01 FAILED login user=admin source=203.0.113.5
2026-06-21 09:00:15 FAILED login user=admin source=203.0.113.5
2026-06-21 09:00:30 FAILED login user=admin source=203.0.113.5
2026-06-21 09:00:45 FAILED login user=admin source=203.0.113.5
2026-06-21 09:01:00 FAILED login user=admin source=203.0.113.5
2026-06-21 09:01:15 SUCCESS login user=admin source=203.0.113.5
2026-06-21 09:05:00 SUCCESS login user=tharsan source=192.168.1.50
EOF
```

## Task 3: Write a Manual Correlation Script (Simulating SIEM Logic)
```python
import re
from collections import defaultdict

failed_attempts = defaultdict(int)
alerts = []

with open("sample_security.log") as f:
    lines = f.readlines()

for i, line in enumerate(lines):
    if "FAILED" in line:
        source = re.search(r'source=(\S+)', line).group(1)
        failed_attempts[source] += 1

    if "SUCCESS" in line:
        source = re.search(r'source=(\S+)', line).group(1)
        if failed_attempts[source] >= 5:
            alerts.append(f"ALERT: Possible brute-force success from {source} after {failed_attempts[source]} failed attempts")

for alert in alerts:
    print(alert)
```

## Task 4: Run and Review
```bash
python3 correlation_check.py
```
Confirm the script correctly flags the brute-force pattern.

## Results
| Item | Value |
|---|---|
| Wazuh preview container running (Y/N) | |
| Sample log created (Y/N) | |
| Correlation script correctly detected the pattern (Y/N) | |
| Alert message generated | |

## Screenshots
```
![Correlation Script Output](Screenshots/correlation-output.png)
![Wazuh Interface Preview](Screenshots/wazuh-preview.png)
```

## Lab Summary
Note that what you just wrote in Python is conceptually exactly what a SIEM's correlation engine does, just manually and at small scale - this should make the real platforms (Wazuh, Splunk) much more intuitive when you reach them in Topics 68-69.
