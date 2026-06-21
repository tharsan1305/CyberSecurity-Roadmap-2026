# Day 35 - Cloud Networking

## Goal
Understand AWS VPC design - subnets, route tables, security groups, and load balancers - the networking layer underneath all AWS services.

---

## 1. VPC Design (Subnets, Route Tables)

A **VPC (Virtual Private Cloud)** is your isolated network within AWS, with a defined CIDR range (e.g., 10.0.0.0/16).

**Subnets** divide the VPC, typically:
- **Public Subnet**: has a route to an Internet Gateway, resources can have public IPs
- **Private Subnet**: no direct route to the internet, used for databases/internal services

**Route Tables** define how traffic is directed within the VPC and to/from the internet.
```
Public subnet route table:
0.0.0.0/0 -> Internet Gateway

Private subnet route table:
0.0.0.0/0 -> NAT Gateway (for outbound-only internet access)
```

## 2. Security Groups & NACLs

**Security Groups**: stateful, instance-level firewall - if you allow inbound traffic, the return outbound traffic is automatically allowed.
```
Inbound rule: Allow TCP 443 from 0.0.0.0/0
Inbound rule: Allow TCP 22 from <your-ip>/32 (never 0.0.0.0/0 for SSH in production)
```

**NACLs (Network Access Control Lists)**: stateless, subnet-level firewall - inbound and outbound rules are evaluated independently, must explicitly allow both directions.

| | Security Group | NACL |
|---|---|---|
| Level | Instance | Subnet |
| State | Stateful | Stateless |
| Rules | Allow only | Allow and Deny |

## 3. Load Balancers (ALB, NLB)

**ALB (Application Load Balancer)**: operates at Layer 7 (HTTP/HTTPS), supports content-based routing (path/host-based rules).

**NLB (Network Load Balancer)**: operates at Layer 4 (TCP/UDP), handles extreme throughput/low latency, preserves source IP.

## 4. VPN/Direct Connect

**Site-to-Site VPN**: connects your on-premises network to AWS VPC over the internet, encrypted (IPSec, ties back to Topic 26).

**Direct Connect**: a dedicated private physical connection to AWS, bypassing the public internet - lower latency, more consistent bandwidth, used by larger enterprises.

---

## Interview Questions

**Q1. Difference between a public and private subnet in a VPC?**
A public subnet has a route to an Internet Gateway (resources can be internet-accessible); a private subnet has no direct internet route, typically used for backend resources like databases.

**Q2. Difference between Security Groups and NACLs?**
Security Groups are stateful and instance-level (allow rules only); NACLs are stateless and subnet-level (both allow and deny rules, evaluated independently for inbound/outbound).

**Q3. When would you choose NLB over ALB?**
When you need Layer 4 (TCP/UDP) handling, extreme performance/low latency, or need to preserve the original source IP - ALB is preferred for HTTP/HTTPS Layer 7 routing.

**Q4. Difference between Site-to-Site VPN and Direct Connect?**
VPN is encrypted connectivity over the public internet; Direct Connect is a dedicated private physical connection, offering more consistent performance.

## Key Takeaways
- Learned VPC design: public/private subnets, route tables
- Learned Security Groups vs NACLs and their stateful/stateless distinction
- Learned ALB vs NLB use cases
- Learned VPN vs Direct Connect for hybrid connectivity
