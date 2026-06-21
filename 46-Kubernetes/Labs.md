# Day 46 - Lab: Kubernetes Hands-On

## Prerequisite: Set Up a Local Cluster
```bash
# Using minikube (simplest local option)
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube start
kubectl get nodes
```

## Task 1: Deploy a Pod Directly
```bash
kubectl run my-app-pod --image=nginx --port=80
kubectl get pods
kubectl describe pod my-app-pod
kubectl delete pod my-app-pod
```

## Task 2: Create a Deployment
```yaml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
```
```bash
kubectl apply -f deployment.yaml
kubectl get deployments
kubectl get pods -o wide
```

## Task 3: Expose via Service
```bash
kubectl expose deployment nginx-deployment --type=NodePort --port=80
kubectl get services
minikube service nginx-deployment --url
curl <returned-url>
```

## Task 4: Test Self-Healing
```bash
kubectl get pods
kubectl delete pod <one-of-the-nginx-pod-names>
kubectl get pods
```
Observe: Kubernetes automatically creates a replacement Pod to maintain the desired replica count.

## Task 5: Scale the Deployment
```bash
kubectl scale deployment nginx-deployment --replicas=5
kubectl get pods
```

## Task 6: Create a Namespace and Deploy Into It
```bash
kubectl create namespace lab-ns
kubectl apply -f deployment.yaml -n lab-ns
kubectl get pods -n lab-ns
```

## Results
| Item | Value |
|---|---|
| Cluster running (Y/N) | |
| Deployment created with 3 replicas (Y/N) | |
| Service accessible via curl (Y/N) | |
| Self-healing confirmed (Y/N) | |
| Scaled to 5 replicas successfully (Y/N) | |
| Namespace deployment successful (Y/N) | |

## Cleanup
```bash
minikube stop
minikube delete
```

## Screenshots
```
![Pods Running](Screenshots/pods-running.png)
![Service Curl Test](Screenshots/service-curl.png)
![Self Healing Test](Screenshots/self-healing.png)
```

## Lab Summary
Note how quickly Kubernetes replaced the deleted Pod, and reflect on what this self-healing behavior means for production reliability versus manually managing individual containers.
