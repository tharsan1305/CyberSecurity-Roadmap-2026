# Day 47 - SonarQube

## Goal
Learn static code analysis for code quality and security - commonly integrated into CI/CD pipelines (Jenkins, from Topic 44) as a quality gate.

---

## 1. Code Quality Analysis

SonarQube performs **static analysis** - examining source code without executing it - to identify bugs, code smells, and maintainability issues.

Metrics tracked:
- **Bugs**: code that will likely produce incorrect behavior
- **Code Smells**: maintainability issues (not necessarily bugs, but bad practice)
- **Coverage**: percentage of code exercised by automated tests
- **Duplications**: repeated code blocks that should be refactored

## 2. Security Vulnerability Detection

SonarQube also flags security issues directly relevant to this roadmap's security focus:
- **Vulnerabilities**: code patterns that could be exploited (e.g., SQL injection-prone code, hardcoded credentials)
- **Security Hotspots**: code that needs manual review to determine if it's actually a security risk in context

This connects directly to the SQL Injection concepts from Topic 31 and the broader OWASP Top 10 (Topic 58) - SonarQube can catch some of these patterns automatically during development, before code ever reaches production.

## 3. Code Smells & Technical Debt

**Code Smell**: a pattern indicating potential maintainability problems (e.g., overly complex functions, duplicated logic, poor naming) - not a bug, but a sign of risk for future bugs.

**Technical Debt**: SonarQube estimates the effort required to fix all identified issues, expressed as time (e.g., "2 days of technical debt") - helps teams prioritize remediation.

## 4. CI/CD Integration

SonarQube integrates into Jenkins pipelines as a **Quality Gate** - a pass/fail checkpoint based on defined thresholds (e.g., "no new critical vulnerabilities," "coverage above 80%").

```groovy
stage('SonarQube Analysis') {
    steps {
        sh 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000'
    }
}
stage('Quality Gate') {
    steps {
        waitForQualityGate abortPipeline: true
    }
}
```

If the Quality Gate fails, the pipeline stops - similar to how failed tests block deployment (Topic 44), but for code quality/security specifically.

---

## Interview Questions

**Q1. What is static code analysis?**
Examining source code for issues without actually executing it - identifying bugs, code smells, and security vulnerabilities through pattern analysis.

**Q2. Difference between a Bug and a Code Smell in SonarQube terminology?**
A Bug is code likely to produce incorrect behavior; a Code Smell is a maintainability issue/bad practice that isn't necessarily incorrect but increases future risk.

**Q3. What is a Security Hotspot?**
Code flagged as needing manual review to determine whether it's actually a security risk in its specific context, as opposed to a definitively confirmed Vulnerability.

**Q4. What is a Quality Gate, and how does it integrate with CI/CD?**
A pass/fail checkpoint based on defined code quality/security thresholds; integrated into a CI/CD pipeline (e.g., Jenkins), it can block deployment if the code doesn't meet the defined standards.

## Key Takeaways
- Learned static code analysis and SonarQube's quality metrics
- Learned the distinction between Vulnerabilities and Security Hotspots
- Learned Code Smells and Technical Debt concepts
- Learned Quality Gate integration into CI/CD pipelines as a deployment blocker
