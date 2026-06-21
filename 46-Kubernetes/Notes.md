# Day 46 - Kubernetes

## Goal
Learn container orchestration at scale - Kubernetes manages deployment, scaling, and operations of containerized applications. This is a large topic; plan 5-7 days of study/lab time, with these notes covering the core building blocks.

---

## 1. Pods, Deployments, Services

**Pod**: the smallest deployable unit in Kubernetes - one or more tightly coupled containers sharing network/storage.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-app-pod
spec:
  containers:
  - name: my-app
    image: my-flask-app:1.0
    ports:
    - containerPort: 5000
```

**Deployment**: manages a set of identical Pods, handling replication, rolling updates, and self-healing (restarting failed Pods).

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app
        image: my-flask-app:1.0
        ports:
        - containerPort: 5000
```

**Service**: provides stable networking to access a set of Pods (since Pod IPs are ephemeral - they change as Pods are recreated).

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-app-service
spec:
  selector:
    app: my-app
  ports:
  - port: 80
    targetPort: 5000
  type: ClusterIP
```

Service types: `ClusterIP` (internal only), `NodePort` (exposes on each node's IP), `LoadBalancer` (provisions an external load balancer, typically in cloud environments).

## 2. ConfigMaps & Secrets

**ConfigMap**: stores non-sensitive configuration data, decoupled from container images.
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  APP_MODE: "production"
```

**Secret**: stores sensitive data (passwords, tokens) - base64 encoded by default (not encrypted by default, just encoded - proper encryption requires additional configuration, an important security nuance).
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: db-secret
type: Opaque
data:
  password: cGFzc3dvcmQxMjM=
```

## 3. Namespaces

Logical partitions within a cluster, isolating resources between teams/environments/projects.

```bash
kubectl create namespace dev
kubectl get pods -n dev
kubectl config set-context --current --namespace=dev
```

Default namespaces: `default`, `kube-system` (system components), `kube-public`.

## 4. Helm Basics

Helm is Kubernetes' package manager - bundles related Kubernetes resources (Deployments, Services, ConfigMaps) into reusable "Charts."

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install my-release bitnami/nginx
helm list
helm uninstall my-release
```

---

## Interview Questions

**Q1. What is the relationship between Pods, Deployments, and Services?**
A Pod runs containers; a Deployment manages multiple replica Pods (scaling, self-healing, updates); a Service provides stable networking to reach those Pods despite their changing IPs.

**Q2. Are Kubernetes Secrets encrypted by default?**
No - they're base64 encoded, not encrypted, by default. Proper encryption at rest requires additional configuration (e.g., enabling encryption providers).

**Q3. What is a Namespace used for?**
Logically partitioning a cluster's resources, commonly used to isolate environments (dev/staging/prod) or teams within the same cluster.

**Q4. What problem does Helm solve?**
It packages related Kubernetes resources into reusable, versioned "Charts," simplifying deployment and management of complex applications compared to applying many individual YAML files manually.

## Key Takeaways
- Learned Pods, Deployments, and Services and how they relate
- Learned ConfigMaps and Secrets, including the important nuance that Secrets are encoded, not encrypted, by default
- Learned Namespaces for resource isolation
- Learned Helm basics for package management
