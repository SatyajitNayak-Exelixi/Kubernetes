# 🐳 Kubernetes : 

This repo contains the kubernetes documenation and practice yaml files to learn Kubernetes 

---

# Kubernetes Cheat Sheet

A quick reference for daily-use Kubernetes commands.

---

## 🔹 Cluster Info

```bash
kubectl version --short                  # Client & Server version
kubectl cluster-info                     # Show cluster info
kubectl get nodes                        # List all nodes
kubectl describe node <node-name>        # Detailed info of a node
```

---

## 🔹 Namespaces

```bash
kubectl get namespaces                   # List namespaces
kubectl create namespace dev             # Create namespace
kubectl delete namespace dev             # Delete namespace
kubectl config set-context --current --namespace=dev   # Switch default namespace
```

---

## 🔹 Pods

```bash
kubectl get pods                         # List Pods
kubectl get pods -o wide                 # Pods with more details
kubectl get pods -w                      # Watch Pods in real-time
kubectl describe pod <pod-name>          # Detailed info about a Pod
kubectl logs <pod-name>                  # View logs of a Pod
kubectl exec -it <pod-name> -- /bin/sh   # Exec into a Pod
kubectl delete pod <pod-name>            # Delete a Pod
```

---

## 🔹 Deployments

```bash
kubectl get deployments                  # List deployments
kubectl create deployment nginx --image=nginx        # Create deployment
kubectl scale deployment nginx --replicas=3          # Scale deployment
kubectl rollout status deployment nginx              # Check rollout status
kubectl rollout undo deployment nginx                # Rollback deployment
kubectl delete deployment nginx                      # Delete deployment
```

---

## 🔹 ReplicaSets

```bash
kubectl get rs                           # List ReplicaSets
kubectl describe rs <rs-name>            # Detailed info
```

---

## 🔹 Services

```bash
kubectl get svc                          # List services
kubectl expose deployment nginx --port=80 --type=NodePort   # Expose app
kubectl describe svc <service-name>      # Detailed info of a Service
kubectl delete svc <service-name>        # Delete a Service
```

---

## 🔹 ConfigMaps & Secrets

```bash
# ConfigMap
kubectl create configmap app-config --from-literal=APP_MODE=prod
kubectl get configmaps
kubectl describe configmap app-config

# Secret
kubectl create secret generic db-secret --from-literal=DB_PASS=password123
kubectl get secrets
kubectl describe secret db-secret
```

---

## 🔹 Storage

```bash
kubectl get pv                           # List Persistent Volumes
kubectl get pvc                          # List Persistent Volume Claims
```

---

## 🔹 Troubleshooting

```bash
kubectl describe pod <pod-name>          # Detailed Pod info
kubectl logs <pod-name>                  # View Pod logs
kubectl exec -it <pod-name> -- /bin/bash # Access Pod shell
kubectl get events --sort-by=.metadata.creationTimestamp   # List events
```

---

## 🔹 Apply / Delete YAML

```bash
kubectl apply -f app.yaml                # Apply config
kubectl apply -f <file-name>.yaml        # Apply config file
kubectl delete -f app.yaml               # Delete resources
```

---

## 🔹 Useful Shortcuts

```bash
kubectl get all                          # List all resources in namespace
kubectl get all -n kube-system           # List system resources
kubectl config view --minify | grep namespace:   # Show current namespace
```

---

✅ **Tip:** Use `kubectl -n <namespace>` to target a specific namespace.
