# Day 25 - Lab: NOC Monitoring Setup

## Objective
Set up a basic monitoring check using free/open-source tools to simulate NOC-style uptime monitoring.

## Task 1: Install Zabbix or Nagios (Choose One)

### Option A: Zabbix (Docker-based quick setup)
```bash
docker run --name zabbix-appliance -d -p 80:80 -p 10051:10051 zabbix/zabbix-appliance:latest
```
Access via browser at `http://localhost`

### Option B: Nagios Core (Linux install)
```bash
sudo apt update
sudo apt install nagios4 -y
```
Access via browser at `http://localhost/nagios4`

## Task 2: Add a Host to Monitor
Configure monitoring for at least one host (can be your own machine, router IP, or a public IP like 8.8.8.8) using ICMP ping checks.

## Task 3: Set a Threshold Alert
Configure an alert to trigger if the host becomes unreachable (downtime simulation - can be tested by stopping the monitored service or disconnecting briefly).

## Task 4: Simulate a Ticket Workflow
Even without a real ticketing tool, write a sample incident ticket manually:
```
Ticket ID: NOC-001
Reported: [date/time]
Issue: Host 192.168.1.1 unreachable
Severity: High
Status: In Progress
Assigned: Tier 1
Resolution Notes: [fill after investigating]
```

## Results
| Item | Value |
|---|---|
| Monitoring tool used | |
| Host(s) added | |
| Alert triggered successfully (Y/N) | |
| Sample ticket created (Y/N) | |

## Screenshots
```
![Monitoring Dashboard](Screenshots/monitoring-dashboard.png)
![Alert Triggered](Screenshots/alert-triggered.png)
```

## Lab Summary
Note how monitoring tool dashboards present uptime data, and how that would translate into a real NOC workflow.
