# Day 33 - AWS Cloud Fundamentals

## Goal
Get oriented in AWS before diving into specific services - global infrastructure, console navigation, and billing awareness.

---

## 1. AWS Global Infrastructure (Regions, AZs)

- **Region**: a geographic area containing multiple data centers (e.g., us-east-1, ap-south-1)
- **Availability Zone (AZ)**: one or more isolated data centers within a region, each with independent power/networking - designing across multiple AZs gives fault tolerance
- **Edge Locations**: smaller sites used by CloudFront (CDN) for content caching closer to users

Choosing a region matters for: latency (closer to users), compliance (data residency laws), and service availability (not all services are in all regions).

## 2. AWS Management Console

The web-based UI for managing AWS resources. Key areas:
- Search bar to find any service
- Region selector (top right) - resources are region-scoped unless global (like IAM)
- Billing dashboard
- CloudShell - browser-based CLI, no local setup needed

## 3. AWS Free Tier Services

Free Tier types:
- **Always Free**: certain limits never expire (e.g., small Lambda usage)
- **12 Months Free**: available for the first year after account creation (e.g., 750 hours/month of t2.micro EC2)
- **Trials**: short-term free access to certain services

Commonly used Free Tier services for learning: EC2 (750 hrs/month t2.micro), S3 (5GB), RDS (750 hrs/month db.t2.micro), Lambda (1M requests/month always free).

## 4. Billing & Cost Management

Critical habit: **set a budget alert immediately** to avoid surprise charges.

```
AWS Console -> Billing -> Budgets -> Create budget
Set: Cost budget, $5 threshold, alert at 80%
```

Also enable: AWS Cost Explorer (visualize spending), Billing alerts via CloudWatch.

**Most common beginner mistake**: leaving an EC2 instance or other resource running after a lab session, leading to unexpected charges. Always stop/terminate resources after labs.

---

## Interview Questions

**Q1. Difference between a Region and an Availability Zone?**
A Region is a broad geographic area; an Availability Zone is an isolated data center (or group of them) within that region, used for fault tolerance.

**Q2. Why would you choose one AWS region over another?**
Latency to users, data residency/compliance requirements, and service/feature availability in that region.

**Q3. What's the first thing you should do after creating an AWS account?**
Enable MFA on the root account and set up a billing budget alert to avoid unexpected charges.

**Q4. What is AWS Free Tier and what are its types?**
A program offering limited free usage of AWS services - Always Free (permanent limits), 12 Months Free (first year), and Trials (short-term).

## Key Takeaways
- Learned AWS global infrastructure: Regions, AZs, Edge Locations
- Learned to navigate the AWS Management Console
- Learned Free Tier types and commonly used free services
- Learned billing/budget alert setup to avoid unexpected costs
