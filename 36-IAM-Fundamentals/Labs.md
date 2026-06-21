# Day 36 - Lab: IAM Users, Groups, Roles, and Policies

## Task 1: Create an IAM Group with a Managed Policy
```bash
aws iam create-group --group-name Developers
aws iam attach-group-policy --group-name Developers --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

## Task 2: Create an IAM User and Add to Group
```bash
aws iam create-user --user-name lab-dev-user
aws iam add-user-to-group --user-name lab-dev-user --group-name Developers
```

## Task 3: Write and Attach a Custom Policy
Create `custom-policy.json`:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:GetObject", "s3:ListBucket"],
      "Resource": ["arn:aws:s3:::my-lab-bucket-*", "arn:aws:s3:::my-lab-bucket-*/*"]
    }
  ]
}
```
```bash
aws iam create-policy --policy-name LabS3ReadOnly --policy-document file://custom-policy.json
aws iam attach-user-policy --user-name lab-dev-user --policy-arn <returned-policy-arn>
```

## Task 4: Create a Role for EC2
1. IAM -> Roles -> Create Role -> Trusted entity: EC2
2. Attach `AmazonS3ReadOnlyAccess`
3. Attach this role to an EC2 instance (or note the steps if not launching one)

## Task 5: Test Policy Enforcement
If you have CLI access as `lab-dev-user` (via generated access keys), attempt an action NOT permitted (e.g., `s3 rm`) and confirm it's denied.

## Results
| Item | Value |
|---|---|
| Group created with policy (Y/N) | |
| User added to group (Y/N) | |
| Custom policy created and attached (Y/N) | |
| EC2 role created (Y/N) | |
| Denied action confirmed (Y/N) | |

## Cleanup
```bash
aws iam delete-user --user-name lab-dev-user
aws iam delete-group --group-name Developers
```

## Screenshots
```
![IAM Group](Screenshots/iam-group.png)
![Custom Policy](Screenshots/custom-policy.png)
![Denied Action](Screenshots/denied-action.png)
```

## Lab Summary
Note what happened when you tried the unauthorized action - confirm the "default deny" principle held true in practice.
