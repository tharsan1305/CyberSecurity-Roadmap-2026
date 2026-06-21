# Day 44 - Lab: Jenkins Pipeline Setup

## Task 1: Install Jenkins (Docker-based, fastest method)
```bash
docker run -d -p 8080:8080 -p 50000:50000 --name jenkins jenkins/jenkins:lts
docker logs jenkins    # find the initial admin password in the output
```
Access at `http://localhost:8080`, enter the admin password, install suggested plugins, create an admin user.

## Task 2: Create a Freestyle Job (Simple Start)
1. New Item -> Freestyle Project -> name it "hello-world-job"
2. Build Steps -> Execute shell: `echo "Hello from Jenkins"`
3. Save and click "Build Now"
4. Check Console Output

## Task 3: Create a Declarative Pipeline Job
1. New Item -> Pipeline -> name it "lab-pipeline"
2. Pipeline script:
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Build stage running'
            }
        }
        stage('Test') {
            steps {
                echo 'Test stage running'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy stage running'
            }
        }
    }
}
```
3. Save, run, observe the pipeline visualization showing each stage.

## Task 4: Connect to a GitHub Repo (Webhook Trigger)
If you have a small test repo with a Jenkinsfile, configure the Pipeline job to pull from SCM (Git) instead of an inline script, and set up a GitHub webhook to trigger builds on push (requires Jenkins to be reachable from GitHub - can use ngrok for local testing).

## Results
| Item | Value |
|---|---|
| Jenkins installed and accessible (Y/N) | |
| Freestyle job ran successfully (Y/N) | |
| Pipeline job with 3 stages ran (Y/N) | |
| GitHub webhook trigger configured (Y/N, optional) | |

## Screenshots
```
![Jenkins Dashboard](Screenshots/jenkins-dashboard.png)
![Pipeline Stage View](Screenshots/pipeline-stages.png)
![Console Output](Screenshots/console-output.png)
```

## Lab Summary
Note how the pipeline stage visualization helped you understand the build process flow, and any setup issues encountered (Docker permission issues are common - resolved via `usermod -aG docker`).
