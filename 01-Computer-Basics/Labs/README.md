# Day 01 - Lab: System Information Gathering

## Objective
Use command-line tools on both Windows and Linux to identify your own system's CPU, RAM, Disk, and OS details, and practice basic network/performance troubleshooting commands.

---

## Task 1: Gather System Information

### Windows Commands
systeminfo

wmic cpu get name

diskmgmt.msc

### Linux Commands
hostnamectl

lscpu

free -h

lsblk

### What to record
- CPU Name
- Number of cores
- Total RAM size
- Disk size and type (HDD/SSD/NVMe)
- OS name and version

---

## Task 2: Network Troubleshooting Practice
ipconfig          (Windows)

ifconfig           (Linux)

ping 8.8.8.8        (test raw connectivity)

ping google.com     (test DNS resolution)

### What to check
- Is an IP address assigned?
- Does ping to 8.8.8.8 succeed?
- Does ping to google.com succeed? (if 8.8.8.8 works but this fails, it's a DNS issue)

---

## Task 3: Performance Check
taskmgr      (Windows - GUI, check Processes/Performance/Startup tabs)

top           (Linux - live CPU/RAM usage per process)

### What to check
- Current CPU usage %
- Current RAM usage %
- Any process consuming unusually high resources

---

## Results

| Item | Value |
|---|---|
| CPU Name | |
| CPU Cores | |
| RAM Size | |
| Disk Size | |
| Disk Type | |
| OS Version | |
| Ping 8.8.8.8 result | |
| Ping google.com result | |
| CPU Usage (idle) | |
| RAM Usage (idle) | |

*(Fill in each row with your own system's actual output)*

--- The end---

## Screenshots
Save command output screenshots in a `Screenshots/` subfolder here, and reference them:
