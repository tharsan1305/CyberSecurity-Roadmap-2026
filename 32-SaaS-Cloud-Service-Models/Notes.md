# Day 32 - SaaS (Cloud Service Models)

## Goal
Understand cloud service and deployment models - the foundation before starting the AWS-focused phase of the roadmap (Topics 33-40).

---

## 1. IaaS vs PaaS vs SaaS

Cloud computing is typically categorized by how much the provider manages versus how much the customer manages.

### IaaS (Infrastructure as a Service)
Provider manages physical hardware, networking, virtualization. Customer manages OS, runtime, applications, data.
Examples: AWS EC2, Azure Virtual Machines, Google Compute Engine

### PaaS (Platform as a Service)
Provider manages infrastructure AND the runtime/OS. Customer manages only the application and data.
Examples: AWS Elastic Beanstalk, Heroku, Azure App Service

### SaaS (Software as a Service)
Provider manages everything - infrastructure, runtime, and the application itself. Customer just uses the software.
Examples: Gmail, Salesforce, Microsoft 365, Slack

Visual comparison:
```
                IaaS    PaaS    SaaS
Application     You     You     Provider
Runtime         You     Provider Provider
OS              You     Provider Provider
Virtualization  Provider Provider Provider
Hardware        Provider Provider Provider
```

## 2. Public vs Private vs Hybrid Cloud

- **Public Cloud**: infrastructure owned/operated by a third party (AWS, Azure, GCP), shared among multiple customers (multi-tenant)
- **Private Cloud**: infrastructure dedicated to a single organization, either on-premises or hosted privately - more control, higher cost
- **Hybrid Cloud**: combination of public and private, allowing data/applications to move between them based on need (e.g., sensitive data stays private, burst workloads go to public cloud)

## 3. Shared Responsibility Model

A critical security concept: cloud security is a shared responsibility between the provider and the customer, and the split changes depending on the service model.

General pattern (using AWS terminology, but applies broadly):
- **Provider is responsible for**: security OF the cloud (physical infrastructure, hypervisor, network controls)
- **Customer is responsible for**: security IN the cloud (data, identity/access management, OS patching for IaaS, application-level security)

```
IaaS:  Customer responsible for OS, app, data, network config, IAM
PaaS:  Customer responsible for app, data, IAM
SaaS:  Customer responsible mainly for data, user access, IAM
```

This model is a frequent interview topic and a frequent source of real-world breaches when misunderstood (e.g., assuming the cloud provider secures your S3 bucket permissions - they don't, you do).

---

## Interview Questions

**Q1. Difference between IaaS, PaaS, and SaaS?**
IaaS provides infrastructure only (you manage OS/app); PaaS provides infrastructure + runtime (you manage just the app); SaaS provides the complete software (you just use it).

**Q2. What is the Shared Responsibility Model?**
A framework defining which security responsibilities belong to the cloud provider versus the customer - the provider secures the underlying cloud infrastructure, while the customer secures their data, access, and configurations within it.

**Q3. Give an example each of IaaS, PaaS, and SaaS.**
IaaS: AWS EC2. PaaS: AWS Elastic Beanstalk / Heroku. SaaS: Gmail / Salesforce.

**Q4. Why does the Shared Responsibility Model matter for security?**
Misunderstanding it is a common cause of real breaches - e.g., assuming the provider secures a customer-configured resource like an S3 bucket, when access control configuration is actually the customer's responsibility.

## Key Takeaways
- Learned the IaaS/PaaS/SaaS spectrum and what each party manages
- Understood Public, Private, and Hybrid cloud deployment models
- Learned the Shared Responsibility Model and why it matters for cloud security
