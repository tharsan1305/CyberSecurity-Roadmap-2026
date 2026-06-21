# Day 51 - Lab: Full DevSecOps Pipeline

## Objective
Build a Jenkins pipeline combining build, SAST (SonarQube), and container scanning (Trivy) - consolidating Topics 43-50 into one security-integrated pipeline.

## Prerequisite
Ensure Jenkins (Topic 44), SonarQube (Topic 47), and Trivy (Topic 40) are still running, or restart their containers:
```bash
docker start jenkins sonarqube
```

## Task 1: Create the Pipeline Job
New Item -> Pipeline -> "devsecops-pipeline"

## Task 2: Write the Jenkinsfile
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Simulating build...'
                sh 'echo "Build complete"'
            }
        }
        stage('SAST Scan') {
            steps {
                echo 'Simulating SonarQube scan...'
                sh 'echo "SAST scan complete - no critical issues (simulated)"'
            }
        }
        stage('Dependency Scan') {
            steps {
                echo 'Simulating dependency scan...'
                sh 'echo "Dependency scan complete (simulated)"'
            }
        }
        stage('Container Scan') {
            steps {
                sh 'docker pull nginx:latest'
                sh 'trivy image nginx:latest --severity HIGH,CRITICAL --exit-code 0'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application (simulated)...'
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished - review all stage results above.'
        }
    }
}
```
(Note: if Jenkins doesn't have Docker/Trivy installed inside its own container, you can run the Container Scan stage's commands manually on the host instead, and document the results - the key learning goal is the pipeline structure.)

## Task 3: Run the Pipeline
Execute and review the stage view, confirming each stage ran in sequence.

## Task 4: Simulate a Failed Gate
Modify the Container Scan stage to use `--exit-code 1` instead of `0` against a deliberately old/vulnerable image, and observe the pipeline fails and stops before reaching Deploy.

## Results
| Item | Value |
|---|---|
| Pipeline created with all 5 stages (Y/N) | |
| Pipeline ran successfully end-to-end (Y/N) | |
| Failed gate test stopped pipeline before Deploy (Y/N) | |

## Screenshots
```
![Pipeline Stages](Screenshots/pipeline-stages.png)
![Failed Gate](Screenshots/failed-gate.png)
```

## Lab Summary
Note how it felt seeing a security scan actually block the deployment stage - write 2-3 lines on why this matters more than a security review that happens only after deployment.
