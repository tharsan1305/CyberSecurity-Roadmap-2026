# Day 45 - Lab: Docker Hands-On

## Task 1: Run Your First Container
```bash
docker run -d -p 8080:80 --name web-test nginx
curl localhost:8080
docker logs web-test
docker stop web-test
docker rm web-test
```

## Task 2: Build a Custom Image
Create a simple Python app:
```bash
mkdir docker-lab && cd docker-lab
cat << 'EOF' > app.py
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello from my Dockerized app, Day 45!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
EOF

echo "flask" > requirements.txt

cat << 'EOF' > Dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "app.py"]
EOF
```
```bash
docker build -t my-flask-app:1.0 .
docker run -d -p 5000:5000 my-flask-app:1.0
curl localhost:5000
```

## Task 3: Use Docker Compose with a Database
```bash
cat << 'EOF' > docker-compose.yml
version: "3.8"
services:
  web:
    build: .
    ports:
      - "5000:5000"
  db:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: labpassword
EOF
```
```bash
docker-compose up -d
docker-compose ps
docker-compose logs
docker-compose down
```

## Task 4: Scan Your Custom Image with Trivy (from Topic 40)
```bash
trivy image my-flask-app:1.0
```
Record any vulnerabilities found.

## Results
| Item | Value |
|---|---|
| First container ran successfully (Y/N) | |
| Custom image built and accessible (Y/N) | |
| Docker Compose multi-container stack ran (Y/N) | |
| Trivy scan results (Critical/High count) | |

## Screenshots
```
![Custom App Running](Screenshots/custom-app.png)
![Docker Compose Status](Screenshots/compose-status.png)
![Trivy Scan](Screenshots/trivy-scan.png)
```

## Lab Summary
Note any vulnerabilities Trivy found in your custom image's base layer (`python:3.11-slim`), and how that connects back to the image scanning concepts from Topic 40.
