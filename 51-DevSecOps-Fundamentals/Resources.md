# Day 51 - Resources

## Tools Used
- Jenkins, SonarQube, Trivy, Docker (all from earlier topics, combined here)
- OWASP Dependency-Check / Snyk (reference, for SCA scanning)
- OWASP ZAP / Burp Suite (reference, for DAST)

## Pipeline Stage Reference
| Stage | Tool Example | Type |
|---|---|---|
| Build | Maven/Jenkins | - |
| SAST | SonarQube | Static code analysis |
| Dependency/SCA Scan | OWASP Dependency-Check, Snyk | Third-party library vulnerabilities |
| Container Scan | Trivy | Image vulnerability scanning |
| DAST | OWASP ZAP, Burp Suite | Runtime application testing |
| Deploy | Jenkins/Kubernetes | - |

## Key Terms Glossary
- **Shift-Left**: moving security activities earlier in the SDLC
- **SAST**: Static Application Security Testing
- **DAST**: Dynamic Application Security Testing
- **SCA**: Software Composition Analysis (dependency scanning)
- **Quality/Security Gate**: automated pass/fail checkpoint in a pipeline

## Further Reading
- OWASP DevSecOps Guideline (owasp.org)
- "DevSecOps" as a discipline - NIST SP 800-218 (Secure Software Development Framework)

## Skills Gained Today
- Full security-integrated CI/CD pipeline design
- Practical SAST + container scanning gate implementation
- Understanding of how earlier roadmap topics (SonarQube, Trivy, Jenkins) combine into one DevSecOps workflow
- Confirmed automated security gates can block deployment, not just report issues
