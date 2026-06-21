# Day 37 - Lab: IAM Hardening

## Task 1: Enable MFA on Your IAM User
Console: IAM -> Users -> your user -> Security credentials -> Assign MFA device (use a virtual MFA app like Google Authenticator/Authy)

## Task 2: Generate and Review Credential Report
```bash
aws iam generate-credential-report
aws iam get-credential-report --query 'Content' --output text | base64 -d > report.csv
cat report.csv
```
Review: any users without MFA, any old/unused access keys.

## Task 3: Write a Least-Privilege Policy (Refine an Overly Broad One)
Start with this overly broad policy:
```json
{ "Effect": "Allow", "Action": "s3:*", "Resource": "*" }
```
Refine it to only allow reading objects from one specific bucket:
```json
{
  "Effect": "Allow",
  "Action": ["s3:GetObject", "s3:ListBucket"],
  "Resource": ["arn:aws:s3:::my-lab-bucket-*", "arn:aws:s3:::my-lab-bucket-*/*"]
}
```
Apply this refined policy to a test user, and verify they can read but not delete/write objects.

## Task 4: Explore IAM Access Analyzer
Console: IAM -> Access Analyzer -> Create Analyzer
Review any findings (may show none in a small lab account, which is also a valid/expected result).

## Task 5: Enforce MFA via Policy (Conceptual/Optional Hands-On)
Write the Deny-without-MFA policy from the Notes and attach it to a test group, then verify actions are blocked without MFA active in the session.

## Results
| Item | Value |
|---|---|
| MFA enabled on your account (Y/N) | |
| Credential report reviewed (Y/N) | |
| Users without MFA found | |
| Least-privilege policy applied and tested (Y/N) | |
| Access Analyzer findings reviewed (Y/N) | |

## Screenshots
```
![MFA Setup](Screenshots/mfa-setup.png)
![Credential Report](Screenshots/credential-report.png)
![Access Analyzer](Screenshots/access-analyzer.png)
```

## Lab Summary
Note how many users (if any in a shared/lab environment) lacked MFA, and reflect on why MFA enforcement matters even for "low-risk" accounts.
