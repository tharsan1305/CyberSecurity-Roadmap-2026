# Day 33 - Lab: AWS Account Setup & Exploration

## Task 1: Account Setup
1. Create AWS Free Tier account (if not done)
2. Enable MFA on root account
3. Create an IAM admin user (don't use root for daily work - covered more Day 36)

## Task 2: Set Budget Alert
AWS Console -> Billing -> Budgets -> Create a $5 budget with 80% alert threshold

## Task 3: Explore Console & CloudShell
```bash
aws sts get-caller-identity
aws ec2 describe-regions --output table
```

## Task 4: Check Free Tier Usage Dashboard
Navigate to Billing -> Free Tier, note what services/limits are tracked.

## Results
| Item | Value |
|---|---|
| Account created (Y/N) | |
| MFA enabled (Y/N) | |
| Budget alert set (Y/N) | |
| CLI identity confirmed (Y/N) | |

## Screenshots
```
![Budget Alert](Screenshots/budget-alert.png)
![CloudShell Output](Screenshots/cloudshell.png)
```

## Lab Summary
Note your account ID and confirm MFA/budget are active before proceeding to hands-on service labs.
