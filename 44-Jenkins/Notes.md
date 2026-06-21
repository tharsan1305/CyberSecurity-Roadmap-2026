# Day 44 - Jenkins

## Goal
Learn Jenkins - the most widely used open-source CI/CD automation server, tying together version control, builds, and deployment.

---

## 1. Pipeline Creation (Declarative/Scripted)

A **Jenkinsfile** defines a pipeline as code, stored alongside the project in version control.

**Declarative Pipeline** (simpler, recommended for most cases):
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
```

**Scripted Pipeline** (more flexible, Groovy-based, older style):
```groovy
node {
    stage('Build') {
        sh 'mvn compile'
    }
    stage('Test') {
        sh 'mvn test'
    }
}
```

## 2. Jobs & Builds

A **Job** (or Pipeline) is a configured task in Jenkins - can be triggered manually, on a schedule (cron-like syntax), or by a webhook (e.g., GitHub push).

Each execution of a job is a **Build**, with its own number, logs, and status (Success, Failure, Unstable).

## 3. Plugins & Integrations

Jenkins' extensibility comes from its plugin ecosystem:
- **Git Plugin**: integrates with Git repositories
- **GitHub Plugin**: webhook-based triggering from GitHub events
- **SonarQube Plugin**: integrates code quality scanning (Topic 47)
- **Docker Plugin**: build/run containers as part of pipelines
- **Credentials Plugin**: securely manage secrets (API keys, passwords) used in pipelines

## 4. Automated Testing Integration

Jenkins pipelines commonly run automated tests as a required gate before allowing deployment:
```groovy
stage('Test') {
    steps {
        sh 'mvn test'
    }
    post {
        always {
            junit 'target/surefire-reports/*.xml'    // publish test results
        }
    }
}
```
If tests fail, the pipeline stops, preventing broken code from being deployed - this is the core value Jenkins (and CI/CD generally) provides.

---

## Interview Questions

**Q1. What is a Jenkinsfile?**
A file defining a Jenkins pipeline as code, typically stored in the project's version control repository alongside the source code.

**Q2. Difference between Declarative and Scripted pipelines?**
Declarative uses a more structured, simpler syntax recommended for most use cases; Scripted uses full Groovy scripting for more complex/flexible logic.

**Q3. What triggers a Jenkins build?**
Manual triggering, scheduled (cron-like) triggers, or webhook-based triggers from version control events like a GitHub push.

**Q4. Why integrate automated testing into a Jenkins pipeline?**
To automatically gate deployments - if tests fail, the pipeline stops, preventing broken or vulnerable code from reaching production.

## Key Takeaways
- Learned Declarative and Scripted Jenkins pipeline syntax
- Learned Jobs/Builds concepts and trigger types
- Learned key Jenkins plugins relevant to this roadmap (Git, SonarQube, Docker, Credentials)
- Learned how automated testing integrates as a deployment gate
