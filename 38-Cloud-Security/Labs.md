# Day 38 - Lab: Cloud Security Monitoring Setup

## Task 1: Enable CloudTrail
```bash
aws cloudtrail create-trail --name lab-trail --s3-bucket-name <your-bucket-for-logs>
aws cloudtrail start-logging --name lab-trail
aws cloudtrail describe-trails
```

## Task 2: Enable GuardDuty
```bash
aws guardduty create-detector --enable
aws guardduty list-detectors
```
Let it run for a while - GuardDuty needs time to establish a baseline before detecting anomalies.

## Task 3: Enable S3 Bucket Encryption
```bash
aws s3api put-bucket-encryption --bucket my-lab-bucket-<yourname> --server-side-encryption-configuration '{"Rules": [{"ApplyServerSideEncryptionByDefault": {"SSEAlgorithm": "AES256"}}]}'
aws s3api get-bucket-encryption --bucket my-lab-bucket-<yourname>
```

## Task 4: Audit Your S3 Buckets for Public Access
Console: S3 -> Block Public Access settings -> confirm "Block all public access" is enabled at the account level (best practice unless you have a specific public-hosting use case).

## Task 5: Review CloudTrail Logs
After performing a few actions (like the ones above), check CloudTrail's Event History in the console - find the log entry for one of your own actions (e.g., the bucket encryption change) and note the fields captured (user, timestamp, source IP, action).

## Results
| Item | Value |
|---|---|
| CloudTrail enabled (Y/N) | |
| GuardDuty enabled (Y/N) | |
| S3 encryption applied (Y/N) | |
| Public access blocked at account level (Y/N) | |
| Own action found in CloudTrail logs (Y/N) | |

## Cleanup
Consider stopping CloudTrail/GuardDuty if not continuing to use them, to avoid any minor cost accumulation outside Free Tier limits (review current Free Tier terms for these services).

## Screenshots
```
![CloudTrail Trail](Screenshots/cloudtrail-trail.png)
![GuardDuty Status](Screenshots/guardduty-status.png)
![S3 Encryption Settings](Screenshots/s3-encryption.png)
```

## Lab Summary
Note what fields CloudTrail captured for your own action, and how that data would help during a real incident investigation.
