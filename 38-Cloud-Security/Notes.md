# Day 38 - Cloud Security

## Goal
Build a broader cloud security picture beyond IAM - encryption, monitoring services, and the most common cloud-specific threats.

---

## 1. Shared Responsibility Model (Revisited)

Recap from Topic 32, now applied concretely:
- AWS secures: physical data centers, hypervisor, network infrastructure
- You secure: data, IAM configuration, OS patching (on EC2/IaaS), application security, network configuration (security groups, NACLs)

## 2. Encryption (KMS, S3 Encryption)

**AWS KMS (Key Management Service)**: manages encryption keys used across AWS services.

S3 encryption options:
- **SSE-S3**: S3-managed keys (simplest)
- **SSE-KMS**: KMS-managed keys (more control, auditing via CloudTrail)
- **SSE-C**: customer-provided keys (you manage the key entirely)

```bash
aws s3api put-bucket-encryption --bucket my-bucket --server-side-encryption-configuration '{"Rules": [{"ApplyServerSideEncryptionByDefault": {"SSEAlgorithm": "aws:kms"}}]}'
```

## 3. Security Monitoring (CloudTrail, GuardDuty)

**CloudTrail**: logs every API call made in your AWS account - who did what, when, from where. Essential for auditing and incident investigation.

**GuardDuty**: AWS's managed threat detection service - analyzes CloudTrail, VPC Flow Logs, and DNS logs for suspicious activity (e.g., API calls from unusual locations, communication with known malicious IPs).

```bash
aws guardduty create-detector --enable
aws cloudtrail describe-trails
```

## 4. Cloud-Specific Threats (Misconfig, Exposed Buckets)

Most common real-world cloud breaches:
- **Public S3 buckets**: sensitive data exposed due to misconfigured bucket policies
- **Overly permissive IAM policies**: wildcard permissions enabling privilege escalation
- **Exposed credentials**: access keys accidentally committed to public GitHub repos (a very common real incident pattern)
- **Unpatched/exposed EC2 instances**: directly internet-facing without proper security groups
- **Misconfigured security groups**: e.g., SSH (port 22) open to 0.0.0.0/0

This is why tools like Cloud Security Posture Management (CSPM, covered Topic 40/CNAPP) exist - to continuously scan for these misconfigurations at scale.

---

## Interview Questions

**Q1. What does CloudTrail log, and why is it important for security?**
Every API call/action taken in an AWS account (who, what, when, from where) - essential for auditing, compliance, and incident investigation.

**Q2. What does GuardDuty do?**
AWS's managed threat detection service that analyzes logs (CloudTrail, VPC Flow Logs, DNS) for suspicious or malicious activity patterns.

**Q3. Name the most common real-world AWS security incident pattern.**
Misconfigured public S3 buckets exposing sensitive data, or leaked access keys (e.g., accidentally committed to a public GitHub repo).

**Q4. Difference between SSE-S3 and SSE-KMS encryption?**
SSE-S3 uses S3-managed keys (simpler); SSE-KMS uses AWS KMS-managed keys, offering more control and detailed audit logging via CloudTrail.

## Key Takeaways
- Reinforced the Shared Responsibility Model with concrete AWS examples
- Learned encryption options via KMS and S3 server-side encryption
- Learned CloudTrail (audit logging) and GuardDuty (threat detection)
- Learned the most common real-world cloud security misconfigurations
