# Day 69 - Lab: Splunk

## Objective
Practice SPL on sample data using Splunk Free Trial or Splunk BOTS (Boss of the SOC) dataset.

## Task 1: Set Up Splunk
Option A: Download Splunk Enterprise Free Trial (splunk.com/free-trial) - 60-day trial
Option B: Use Splunk's online trial environment (no install needed)

## Task 2: Load Sample Data
In Splunk: Settings -> Add Data -> Upload. Upload a sample log file (your auth.log from Topic 67 works well, or Splunk's built-in tutorial data).

## Task 3: Basic SPL Practice
```splunk
index=main | head 100
index=main "Failed" | stats count by host
index=main | rex field=_raw "from (?P<src_ip>\d+\.\d+\.\d+\.\d+)" | stats count by src_ip | sort -count
```

## Task 4: Create a Dashboard Panel
Run a stats search, save it as a report, add it to a new dashboard.

## Task 5: Create a Scheduled Alert
Create a saved search that runs every 5 minutes, alerts if more than 5 events contain "Failed password."

## Results
| Item | Value |
|---|---|
| Splunk running (Y/N) | |
| Data indexed (Y/N) | |
| SPL queries working (Y/N) | |
| Dashboard panel created (Y/N) | |
| Alert configured (Y/N) | |

## Lab Summary
Note what was different/similar between Splunk SPL and the grep/awk log parsing you did in Topic 67.
