# Day 40 - Lab: Container Image Scanning (Preview, full Docker lab in Topic 45)

## Objective
Get a first hands-on look at container vulnerability scanning. Full Docker setup happens in Topic 45 - today uses minimal setup just to demonstrate scanning.

## Task 1: Install Docker (Minimal, if not already done)
```bash
sudo apt install docker.io -y
sudo systemctl start docker
sudo usermod -aG docker $(whoami)
# log out/in for group change to take effect
```

## Task 2: Install Trivy
```bash
sudo apt-get install wget apt-transport-https gnupg lsb-release -y
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo "deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy -y
```

## Task 3: Scan a Public Image
```bash
docker pull nginx:latest
trivy image nginx:latest
```
Record: number of vulnerabilities found by severity (Critical/High/Medium/Low).

## Task 4: Scan an Older/Known-Vulnerable Image (for comparison)
```bash
trivy image nginx:1.14
```
Compare vulnerability counts against the latest version - older images typically show significantly more.

## Task 5: Research CSPM Tools (Conceptual)
Research one free/open-source CSPM tool (e.g., Prowler for AWS, ScoutSuite) and note what kind of misconfigurations it checks for.

## Results
| Item | Value |
|---|---|
| Trivy installed (Y/N) | |
| nginx:latest vulnerabilities (Critical/High count) | |
| nginx:1.14 vulnerabilities (Critical/High count) | |
| CSPM tool researched | |

## Screenshots
```
![Trivy Scan Output](Screenshots/trivy-scan.png)
![Vulnerability Comparison](Screenshots/vuln-comparison.png)
```

## Lab Summary
Note the vulnerability count difference between the latest and older image versions - this makes the "keep images updated" security practice concrete rather than abstract.
