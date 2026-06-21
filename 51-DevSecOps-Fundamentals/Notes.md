# Day 51 - DevSecOps Fundamentals

## Goal
Bring together everything from the DevOps phase (Topics 41-50) with security - this is where the roadmap's "DevOps" and "Security" tracks formally merge, directly relevant to many real job titles you may be targeting.

---

## 1. Shift-Left Security

The core DevSecOps principle: integrate security as early as possible in the SDLC (Topic 42), rather than only at the end.

```
Traditional: Plan -> Design -> Develop -> Test -> [Security Review] -> Deploy
Shift-Left:  Plan -> [Security] Design -> [Security] Develop -> [Security] Test -> Deploy
```

"Shift-left" refers to moving security activities leftward on the timeline (toward planning/development) rather than treating it as a final gate.

## 2. Security in CI/CD Pipeline

Building on Jenkins (Topic 44) and SonarQube (Topic 47), a DevSecOps pipeline adds security checks as automated gates:

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps { sh 'mvn compile' }
        }
        stage('SAST Scan') {
            steps { sh 'mvn sonar:sonar' }
        }
        stage('Dependency Scan') {
            steps { sh 'mvn dependency-check:check' }
        }
        stage('Container Scan') {
            steps { sh 'trivy image my-app:latest' }
        }
        stage('Deploy') {
            steps { echo 'Deploying...' }
        }
    }
}
```

## 3. SAST/DAST Tools

**SAST (Static Application Security Testing)**: analyzes source code without running it - SonarQube (Topic 47) is a SAST tool. Catches issues early, before the application even runs.

**DAST (Dynamic Application Security Testing)**: tests a running application from the outside, simulating attacks - similar to how a pentester would approach a live web app (foreshadowing Topic 62, Web Pentesting). Tools: OWASP ZAP, Burp Suite.

| | SAST | DAST |
|---|---|---|
| When | Before runtime (source code) | Against running application |
| Finds | Code-level issues | Runtime/configuration issues |
| Example tool | SonarQube | OWASP ZAP |

## 4. Container/Dependency Scanning

Already covered hands-on:
- **Container scanning**: Trivy (Topic 40/45) - scans container images for known vulnerabilities
- **Dependency scanning**: checks third-party libraries (Maven dependencies from Topic 43) against vulnerability databases - tools like OWASP Dependency-Check, Snyk

This is where the roadmap's earlier security scripting (Topic 13), SQL injection prevention (Topic 31), and AWS security (Topic 38) all connect into one continuous automated pipeline rather than isolated manual checks.

---

## Interview Questions

**Q1. What does "Shift-Left Security" mean?**
Integrating security practices earlier in the SDLC (design, development) rather than treating it as a final gate before deployment - catching issues when they're cheaper and easier to fix.

**Q2. Difference between SAST and DAST?**
SAST analyzes source code statically, without execution; DAST tests a running application dynamically, simulating real attacks from the outside.

**Q3. Name three types of automated security scans you'd add to a CI/CD pipeline.**
SAST (code analysis, e.g., SonarQube), dependency/SCA scanning (e.g., OWASP Dependency-Check), and container image scanning (e.g., Trivy).

**Q4. Why integrate security scans as automated pipeline gates rather than manual reviews?**
Automated gates catch issues consistently and immediately on every change, scale better than manual review, and prevent vulnerable code from progressing further in the pipeline without requiring a dedicated security reviewer for every commit.

## Key Takeaways
- Learned Shift-Left Security as the core DevSecOps principle
- Learned how to structure a security-integrated CI/CD pipeline
- Learned SAST vs DAST and their respective tools
- Connected container and dependency scanning into the full automated pipeline picture
