# Day 37 - IAM Security

## Goal
Go beyond IAM basics into hardening practices - least privilege enforcement, MFA, auditing, and cross-account access patterns commonly tested in Cloud Security interviews.

---

## 1. Least Privilege Principle

Grant only the minimum permissions needed to perform a task - nothing more.

Practical approach:
1. Start with no permissions
2. Add only what's explicitly needed
3. Use AWS IAM Access Analyzer to identify unused permissions over time
4. Avoid wildcard permissions (`"Action": "*"`, `"Resource": "*"`) in production policies

Bad example (overly broad):
```json
{ "Effect": "Allow", "Action": "*", "Resource": "*" }
```
Better example (scoped):
```json
{ "Effect": "Allow", "Action": "s3:GetObject", "Resource": "arn:aws:s3:::specific-bucket/*" }
```

## 2. MFA (Multi-Factor Authentication)

Adds a second verification factor beyond password - critical for root accounts and privileged IAM users.

```bash
aws iam enable-mfa-device --user-name <username> --serial-number <device-arn> --authentication-code1 <code1> --authentication-code2 <code2>
```

Can also enforce MFA via policy condition:
```json
{
  "Effect": "Deny",
  "Action": "*",
  "Resource": "*",
  "Condition": {"BoolIfExists": {"aws:MultiFactorAuthPresent": "false"}}
}
```

## 3. Policy Auditing & Access Analyzer

**IAM Access Analyzer**: identifies resources shared with external entities (e.g., an S3 bucket accidentally accessible from outside your account) and can generate least-privilege policies based on actual CloudTrail activity.

**Credential Report**: a downloadable report showing all IAM users, their password/access key age, MFA status - useful for periodic security audits.
```bash
aws iam generate-credential-report
aws iam get-credential-report
```

## 4. Cross-Account Access

Allows a user/role in one AWS account to access resources in another, without creating duplicate IAM users - done via Role assumption with a trust policy.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {"AWS": "arn:aws:iam::ACCOUNT-B-ID:root"},
      "Action": "sts:AssumeRole"
    }
  ]
}
```

---

## Interview Questions

**Q1. What is the Principle of Least Privilege and why does it matter?**
Granting only the minimum permissions necessary - it limits the blast radius if credentials are compromised or misused.

**Q2. How can you enforce MFA usage via IAM policy rather than just account settings?**
Using a Deny statement with a Condition checking `aws:MultiFactorAuthPresent` is false, blocking actions when MFA wasn't used.

**Q3. What does IAM Access Analyzer help identify?**
Resources unintentionally shared with external entities, and can suggest least-privilege policies based on actual usage patterns.

**Q4. How does cross-account access typically work in AWS?**
Via Role assumption - a trust policy in the target account allows a specified principal (user/role) from another account to assume that role temporarily.

## Key Takeaways
- Learned practical application of least privilege in IAM policies
- Learned MFA enforcement, both via account settings and policy conditions
- Learned IAM Access Analyzer and Credential Reports for auditing
- Learned cross-account access via Role assumption and trust policies
