# Day 44 - Resources

## Tools Used
- Jenkins (Docker-based installation: `jenkins/jenkins:lts`)

## Commands Reference
| Purpose | Command |
|---|---|
| Run Jenkins via Docker | `docker run -d -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts` |
| View Jenkins logs | `docker logs jenkins` |
| Restart Jenkins container | `docker restart jenkins` |

## Key Terms Glossary
- **Jenkinsfile**: pipeline-as-code definition file
- **Stage**: a logical division of a pipeline (Build, Test, Deploy, etc.)
- **Agent**: the machine/environment where pipeline steps execute
- **Webhook**: an HTTP callback triggering a build on a version control event

## Further Reading
- Jenkins official documentation (jenkins.io/doc)
- Jenkins Pipeline Syntax reference (built into Jenkins UI under Pipeline Syntax)

## Skills Gained Today
- Jenkins installation and initial setup
- Freestyle and Declarative Pipeline job creation
- Pipeline stage structuring
- GitHub webhook integration awareness
