# Day 47 - Resources

## Tools Used
- SonarQube (Community Edition via Docker)
- SonarScanner / Maven SonarQube plugin

## Commands Reference
| Purpose | Command |
|---|---|
| Run SonarQube via Docker | `docker run -d -p 9000:9000 sonarqube:lts-community` |
| Scan a Maven project | `mvn sonar:sonar -Dsonar.host.url=<url> -Dsonar.login=<token>` |

## Key Terms Glossary
- **Static Analysis**: examining code without executing it
- **Code Smell**: maintainability concern, not necessarily a bug
- **Security Hotspot**: code requiring manual review for security risk
- **Quality Gate**: pass/fail threshold checkpoint integrated into CI/CD
- **Technical Debt**: estimated effort to resolve all flagged issues

## Further Reading
- SonarQube official documentation (docs.sonarsource.com)
- OWASP correlation: many SonarQube security rules map directly to OWASP Top 10 categories (relevant ahead of Topic 58)

## Skills Gained Today
- SonarQube setup and project scanning
- Interpretation of Bugs, Vulnerabilities, Code Smells, Coverage metrics
- Quality Gate concept for CI/CD integration
- Practical confirmation that static analysis catches real security anti-patterns
