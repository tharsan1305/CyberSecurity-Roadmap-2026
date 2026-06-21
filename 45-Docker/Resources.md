# Day 45 - Resources

## Tools Used
- Docker Engine
- Docker Compose
- Trivy (image scanning, from Topic 40)

## Commands Reference
| Purpose | Command |
|---|---|
| Pull image | `docker pull <image>:<tag>` |
| List images | `docker images` |
| Run container | `docker run -d -p <host>:<container> <image>` |
| List running containers | `docker ps` |
| List all containers | `docker ps -a` |
| Stop container | `docker stop <id>` |
| Remove container | `docker rm <id>` |
| Build image | `docker build -t <name>:<tag> .` |
| View logs | `docker logs <id>` |
| Compose up | `docker-compose up -d` |
| Compose down | `docker-compose down` |
| Create volume | `docker volume create <name>` |
| List networks | `docker network ls` |

## Key Terms Glossary
- **Image**: read-only template for creating containers
- **Container**: a running instance of an image
- **Dockerfile**: build instructions for a custom image
- **Volume**: persistent storage outliving container lifecycle
- **Docker Compose**: tool for defining multi-container applications via YAML

## Further Reading
- Docker official documentation and "Get Started" guide (docs.docker.com)
- Docker Hub (hub.docker.com) - public image registry

## Skills Gained Today
- Image pulling, running, and container lifecycle management
- Custom Dockerfile authoring and image building
- Multi-container orchestration with Docker Compose
- Volume and networking fundamentals
- Connected image scanning practice from Topic 40 to a real custom image
