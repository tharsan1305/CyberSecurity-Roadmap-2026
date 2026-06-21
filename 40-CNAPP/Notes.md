# Day 40 - Container & Cloud-Native Security (CNAPP)

## Goal
Understand security for containerized/cloud-native environments - this connects the Cloud phase to the upcoming Docker/Kubernetes phase (Topics 45-46).

---

## 1. Container Image Scanning

Container images can contain vulnerable OS packages, outdated libraries, or embedded secrets. Image scanning analyzes images (before or after deployment) against known vulnerability databases (CVEs).

Common tools: Trivy (free, open-source), Clair, Snyk, AWS ECR built-in scanning.

```bash
# Trivy example (covered hands-on once Docker is set up in Topic 45)
trivy image nginx:latest
```

This should run as part of CI/CD pipelines (ties to DevSecOps, Topic 51) - catching vulnerable images before they reach production.

## 2. Kubernetes Security Posture

Kubernetes-specific security concerns:
- **RBAC misconfiguration**: overly permissive roles granting excessive cluster access
- **Exposed Kubernetes Dashboard/API**: a historically common real-world breach vector when left unauthenticated
- **Pod Security Standards**: restricting what containers can do (e.g., preventing privileged containers, root execution)
- **Network Policies**: Kubernetes' equivalent of micro-segmentation (ties back to Zero Trust, Topic 27) - controlling which pods can communicate with which

## 3. Runtime Protection

Monitoring containers/workloads while they're actively running, not just scanning images beforehand - detecting anomalous behavior (e.g., a container unexpectedly spawning a shell, making unusual network connections).

Tools: Falco (open-source runtime security), commercial CNAPP platforms (Wiz, Prisma Cloud, Aqua Security).

## 4. CSPM (Cloud Security Posture Management)

Continuously scans cloud environments (AWS/Azure/GCP) for misconfigurations against best-practice benchmarks (e.g., CIS Benchmarks) - directly addresses the "exposed S3 bucket" / "overly permissive IAM" problems from Topic 38, but at automated scale across an entire cloud estate.

**CNAPP (Cloud-Native Application Protection Platform)** is the umbrella term combining CSPM + container/image scanning + runtime protection + IAM risk analysis into one platform - the modern, consolidated approach vendors are moving toward.

---

## Interview Questions

**Q1. What is container image scanning, and when should it happen?**
Analyzing container images for known vulnerabilities (CVEs) and embedded secrets, ideally integrated into the CI/CD pipeline before deployment to production.

**Q2. What is a common real-world Kubernetes security mistake?**
Leaving the Kubernetes Dashboard or API server exposed without proper authentication, or overly permissive RBAC roles granting excessive access.

**Q3. Difference between image scanning and runtime protection?**
Image scanning checks for vulnerabilities before deployment (static); runtime protection monitors actively running containers for anomalous behavior (dynamic).

**Q4. What does CSPM do, and what does CNAPP add on top of it?**
CSPM continuously scans cloud configurations for misconfigurations; CNAPP combines CSPM with container scanning, runtime protection, and IAM risk analysis into one consolidated platform.

## Key Takeaways
- Learned container image scanning concepts and tools
- Learned Kubernetes-specific security risks (RBAC, exposed dashboards, network policies)
- Learned runtime protection as a complement to static image scanning
- Learned CSPM and CNAPP as consolidated cloud-native security approaches
