# Day 36 - IAM Fundamentals

## Goal
Learn AWS Identity and Access Management - arguably the single most security-critical AWS service, controlling who can do what.

---

## 1. Users, Groups, Roles

- **IAM User**: represents a person or application with long-term credentials (password and/or access keys)
- **IAM Group**: a collection of users, used to apply permissions collectively rather than per-user
- **IAM Role**: a set of permissions that can be assumed temporarily - by users, AWS services (e.g., an EC2 instance), or external identities. No long-term credentials; uses temporary security tokens

Best practice: prefer Roles over long-lived access keys wherever possible (e.g., an EC2 instance accessing S3 should use an IAM Role, not embedded access keys).

## 2. Policies (JSON Structure)

Policies are JSON documents defining permissions.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-bucket/*"
    }
  ]
}
```

Key elements:
- **Effect**: Allow or Deny
- **Action**: the specific API operation(s)
- **Resource**: the AWS resource(s) the policy applies to, identified by ARN (Amazon Resource Name)
- **Condition** (optional): further restricts when the policy applies (e.g., only from a specific IP)

## 3. Permissions & Access Levels

Policy types:
- **AWS Managed Policies**: pre-built by AWS (e.g., `AmazonS3ReadOnlyAccess`)
- **Customer Managed Policies**: custom policies you create
- **Inline Policies**: attached directly to a single user/group/role, not reusable

Permission evaluation logic: by default, everything is denied; an explicit Allow is required; an explicit Deny always overrides any Allow.

## 4. Identity Federation

Allows users to authenticate using an external identity provider (e.g., corporate Active Directory, Google, SAML-based SSO) instead of creating separate AWS IAM users - ties back to Zero Trust/identity-centric security concepts from Topic 27.

---

## Interview Questions

**Q1. Difference between an IAM User and an IAM Role?**
A User has long-term credentials tied to a specific identity; a Role provides temporary credentials that can be assumed by users, services, or external identities as needed.

**Q2. What does an IAM Policy's "Effect" field control?**
Whether the statement Allows or Denies the specified action(s).

**Q3. If a user has an explicit Allow from one policy and an explicit Deny from another, what happens?**
The explicit Deny always wins, regardless of any Allow statements.

**Q4. Why prefer IAM Roles over long-lived access keys for an application running on EC2?**
Roles provide temporary, automatically-rotated credentials, reducing the risk of credential leakage compared to embedding static access keys in code/config.

## Key Takeaways
- Learned IAM Users, Groups, and Roles and when to use each
- Learned IAM Policy JSON structure (Effect, Action, Resource, Condition)
- Learned policy types and the default-deny/explicit-deny-wins evaluation logic
- Learned Identity Federation for external identity provider integration
