# Day 13 - Lab: Python Practice

## Objective
Write small practical Python scripts covering syntax, OOP, file handling, and a basic security automation task.

## Task 1: Basic Script
Write a script that takes a list of numbers and prints which are even/odd:
```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
for n in numbers:
    if n % 2 == 0:
        print(f"{n} is even")
    else:
        print(f"{n} is odd")
```

## Task 2: OOP - Build a Simple Asset Tracker
```python
class Asset:
    def __init__(self, name, ip, asset_type):
        self.name = name
        self.ip = ip
        self.asset_type = asset_type

    def __str__(self):
        return f"[{self.asset_type}] {self.name} - {self.ip}"

assets = [
    Asset("Web Server", "192.168.1.10", "Server"),
    Asset("Laptop-01", "192.168.1.50", "Workstation"),
]

for a in assets:
    print(a)
```

## Task 3: File Handling - Write a Simple Note Logger
```python
def log_note(note):
    with open("daily_notes.txt", "a") as f:
        f.write(f"{note}\n")

log_note("Day 13: Learned Python OOP and file handling")

with open("daily_notes.txt") as f:
    print(f.read())
```

## Task 4: Security Scripting - Failed Login Counter
Create a sample log file `auth_sample.log`:
```
2026-06-21 10:00:01 SUCCESS login user=admin
2026-06-21 10:01:15 FAILED login user=admin
2026-06-21 10:01:20 FAILED login user=admin
2026-06-21 10:02:00 SUCCESS login user=tharsan
2026-06-21 10:03:45 FAILED login user=root
```
Write a script to count and print failed login attempts and the associated usernames:
```python
import re

failed_count = 0
with open("auth_sample.log") as f:
    for line in f:
        if "FAILED" in line:
            failed_count += 1
            user_match = re.search(r'user=(\w+)', line)
            if user_match:
                print(f"Failed login: {user_match.group(1)}")

print(f"Total failed logins: {failed_count}")
```

## Results
| Item | Value |
|---|---|
| Even/odd script works (Y/N) | |
| Asset tracker output | |
| Notes logged successfully (Y/N) | |
| Failed login count | |

## Screenshots
```
![Asset Tracker Output](Screenshots/asset-tracker.png)
![Failed Login Script](Screenshots/failed-login-script.png)
```

## Lab Summary
Note which concept (OOP vs file handling vs regex parsing) felt most natural, and which needs more practice.
