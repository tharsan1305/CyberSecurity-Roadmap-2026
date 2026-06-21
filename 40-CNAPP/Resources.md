# Day 40 - Resources

## Tools Used
- Trivy (open-source container vulnerability scanner)
- Docker (minimal setup, full coverage in Topic 45)
- Prowler / ScoutSuite (CSPM tools, reference)
- Falco (open-source runtime security, reference)

## Commands Reference
| Purpose | Command |
|---|---|
| Install Trivy | See multi-step setup in Labs.md |
| Scan an image | `trivy image <image-name>:<tag>` |
| Pull a Docker image | `docker pull <image>:<tag>` |

## Key Terms Glossary
- **CVE**: Common Vulnerabilities and Exposures, standardized vulnerability identifiers
- **CSPM**: Cloud Security Posture Management
- **CNAPP**: Cloud-Native Application Protection Platform
- **RBAC**: Role-Based Access Control (also applies within Kubernetes, not just cloud IAM)
- **Runtime Protection**: monitoring actively running workloads for malicious behavior

## Further Reading
- Trivy official documentation (aquasecurity.github.io/trivy)
- CIS Benchmarks (cisecurity.org) - the standard misconfiguration baseline CSPM tools check against
- Kubernetes official security documentation

## Skills Gained Today
- Container image vulnerability scanning with Trivy
- Understanding of CSPM and CNAPP concepts
- Awareness of Kubernetes-specific security risks ahead of the Kubernetes phase (Topic 46)
