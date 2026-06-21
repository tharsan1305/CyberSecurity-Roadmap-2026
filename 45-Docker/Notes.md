# Day 45 - Docker

## Goal
Learn containerization fundamentals - Docker is foundational for Kubernetes (next topic), CI/CD pipelines, and modern application deployment generally. Plan 2-3 days for this topic given its depth.

---

## 1. Images & Containers

**Image**: a read-only template containing application code, runtime, libraries, and dependencies - the "blueprint."

**Container**: a running instance of an image - isolated, lightweight, sharing the host OS kernel (unlike a full VM).

```bash
docker pull nginx:latest          # download an image
docker images                       # list local images
docker run -d -p 8080:80 nginx        # run a container from the image
docker ps                               # list running containers
docker ps -a                              # list all containers (including stopped)
docker stop <container-id>
docker rm <container-id>
```

## 2. Dockerfile

A text file with instructions to build a custom image.

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "app.py"]
```

Build and run:
```bash
docker build -t my-app:1.0 .
docker run -d -p 5000:5000 my-app:1.0
```

Key instructions: `FROM` (base image), `WORKDIR` (working directory), `COPY` (copy files in), `RUN` (execute build-time commands), `EXPOSE` (document port), `CMD` (default runtime command).

## 3. Docker Compose

Defines and runs multi-container applications using a single YAML file.

```yaml
version: "3.8"
services:
  web:
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - db
  db:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: example
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
```

```bash
docker-compose up -d
docker-compose down
docker-compose logs
```

## 4. Volumes & Networking

**Volumes**: persistent storage that survives container restarts/removal (containers themselves are ephemeral by design).
```bash
docker volume create my_data
docker run -v my_data:/app/data my-app:1.0
```

**Networking**: containers communicate via Docker networks. By default, Compose creates a network where services can reach each other by service name (e.g., the `web` service connects to `db` using hostname `db`).

```bash
docker network ls
docker network create my-network
docker run --network my-network my-app:1.0
```

Security note: never run containers as root unless necessary, avoid embedding secrets in Dockerfiles (use environment variables or secret management instead), and keep base images updated (ties to Trivy scanning from Topic 40).

---

## Interview Questions

**Q1. Difference between a Docker image and a container?**
An image is a static, read-only template; a container is a running (or stopped) instance created from that image.

**Q2. Why are containers considered more lightweight than virtual machines?**
Containers share the host OS kernel rather than virtualizing an entire OS, making them faster to start and less resource-intensive than full VMs.

**Q3. What is the purpose of a Dockerfile?**
A set of instructions defining how to build a custom Docker image - base image, dependencies, files to copy, and the default startup command.

**Q4. Why are Docker volumes needed?**
Containers are ephemeral by design (data is lost when removed); volumes provide persistent storage that survives container restarts or removal.

## Key Takeaways
- Learned the distinction between images and containers
- Learned Dockerfile syntax and image building
- Learned Docker Compose for multi-container applications
- Learned volumes for persistence and Docker networking basics
- Learned baseline container security practices
