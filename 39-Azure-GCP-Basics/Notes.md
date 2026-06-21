# Day 39 - Azure/GCP Basics (Multi-Cloud Awareness)

## Goal
Build cross-cloud awareness - many organizations use multiple clouds, and interviewers expect you to map AWS concepts onto Azure/GCP equivalents.

---

## 1. Azure Core Services

| AWS Equivalent | Azure Service | Purpose |
|---|---|---|
| EC2 | Virtual Machines | Compute |
| S3 | Blob Storage | Object storage |
| IAM | Entra ID (formerly Azure AD) | Identity and access management |
| VPC | Virtual Network (VNet) | Networking |
| RDS | Azure SQL Database | Managed database |
| Lambda | Azure Functions | Serverless |

**Entra ID** specifically is worth knowing well - it's Microsoft's identity platform, central to enterprise environments already using Active Directory (ties back to Topic 05), and commonly the IAM backbone for organizations that are Microsoft-centric.

## 2. GCP Core Services

| AWS Equivalent | GCP Service | Purpose |
|---|---|---|
| EC2 | Compute Engine | Compute |
| S3 | Cloud Storage | Object storage |
| IAM | Cloud IAM | Identity and access management |
| VPC | VPC (same name) | Networking |
| RDS | Cloud SQL | Managed database |
| Lambda | Cloud Functions | Serverless |

GCP is generally considered strong in data analytics/ML tooling (BigQuery, Vertex AI) - relevant context given the AI phase later in this roadmap.

## 3. Cross-Cloud Comparison

Key differences to be aware of:
- **Azure**: deeply integrated with Microsoft enterprise tools (AD, Office 365), often the default choice for Microsoft-centric organizations
- **GCP**: strong in data/ML/analytics, often chosen by data-heavy or Kubernetes-native organizations (Kubernetes itself originated at Google)
- **AWS**: largest market share, broadest service catalog, most mature ecosystem and third-party tooling support

For security roles specifically, the core concepts transfer directly across all three: IAM/least privilege, encryption, network segmentation, logging/monitoring - just with different service names and console layouts.

---

## Interview Questions

**Q1. What is Azure's equivalent to AWS IAM?**
Microsoft Entra ID (formerly Azure Active Directory).

**Q2. What is GCP's equivalent to AWS S3?**
Cloud Storage.

**Q3. Why might an organization choose Azure over AWS?**
Deep integration with existing Microsoft enterprise tools (Active Directory, Office 365) if already a Microsoft-centric environment.

**Q4. What underlying security concepts transfer across all three major cloud providers?**
IAM/least privilege principles, encryption practices, network segmentation, and centralized logging/monitoring - the specific tools differ, but the principles are universal.

## Key Takeaways
- Learned Azure core services and their AWS equivalents
- Learned GCP core services and their AWS equivalents
- Understood each provider's relative strengths (Azure: Microsoft integration, GCP: data/ML, AWS: market maturity)
- Reinforced that core cloud security principles are provider-agnostic
