# Day 46 - Resources

## Tools Used
- minikube (local Kubernetes cluster)
- kubectl (Kubernetes CLI)
- Helm (package manager)

## Commands Reference
| Purpose | Command |
|---|---|
| Start local cluster | `minikube start` |
| List nodes | `kubectl get nodes` |
| Apply a manifest | `kubectl apply -f file.yaml` |
| List pods | `kubectl get pods` |
| Describe a resource | `kubectl describe pod <name>` |
| Delete a resource | `kubectl delete pod <name>` |
| Expose a deployment | `kubectl expose deployment <name> --type=NodePort --port=<port>` |
| Scale a deployment | `kubectl scale deployment <name> --replicas=<n>` |
| Create namespace | `kubectl create namespace <name>` |
| Switch namespace context | `kubectl config set-context --current --namespace=<name>` |

## Key Terms Glossary
- **Pod**: smallest deployable unit, one or more containers
- **Deployment**: manages replica Pods, handles scaling/self-healing
- **Service**: stable network endpoint for accessing Pods
- **Namespace**: logical cluster partition
- **Helm Chart**: packaged, reusable Kubernetes resource bundle

## Further Reading
- Kubernetes official documentation (kubernetes.io/docs)
- "Kubernetes Up & Running" (O'Reilly, widely recommended reference book)
- Killer.sh / KillerCoda (free interactive Kubernetes practice scenarios)

## Skills Gained Today
- Local Kubernetes cluster setup with minikube
- Pod, Deployment, and Service creation and management
- Self-healing and scaling behavior observation
- Namespace-based resource isolation
- ConfigMap/Secret awareness (including the encoding vs encryption nuance)
