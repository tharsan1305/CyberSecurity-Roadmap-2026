# Day 47 - Lab: SonarQube Code Scanning

## Task 1: Run SonarQube via Docker
```bash
docker run -d --name sonarqube -p 9000:9000 sonarqube:lts-community
```
Access at `http://localhost:9000` (default login: admin/admin, you'll be prompted to change it).

## Task 2: Generate a Project Token
In SonarQube UI: My Account -> Security -> Generate a token, save it for use in the next step.

## Task 3: Scan the Maven Project from Topic 43
Install the SonarScanner, or use the Maven plugin directly:
```bash
cd my-app   # from Topic 43's lab
mvn sonar:sonar -Dsonar.projectKey=my-app -Dsonar.host.url=http://localhost:9000 -Dsonar.login=<your-token>
```

## Task 4: Review Results in the Dashboard
Open the project in SonarQube UI:
- Note Bugs, Vulnerabilities, Code Smells, and Coverage percentage
- Click into any flagged issue to see the specific line and explanation

## Task 5: Intentionally Introduce a Vulnerability and Re-Scan
Add a deliberately bad code pattern (e.g., a hardcoded password string in a Java file):
```java
String password = "admin123";  // intentional bad practice for testing
```
Re-run the scan and confirm SonarQube flags it.

## Results
| Item | Value |
|---|---|
| SonarQube running and accessible (Y/N) | |
| Project scanned successfully (Y/N) | |
| Bugs/Vulnerabilities/Code Smells found | |
| Intentional vulnerability detected (Y/N) | |

## Cleanup
```bash
docker stop sonarqube
docker rm sonarqube
```

## Screenshots
```
![SonarQube Dashboard](Screenshots/sonarqube-dashboard.png)
![Issues List](Screenshots/issues-list.png)
![Detected Vulnerability](Screenshots/detected-vuln.png)
```

## Lab Summary
Note whether SonarQube successfully caught your intentionally introduced hardcoded password issue, and what category it was classified under (likely a Security Hotspot or Vulnerability).
