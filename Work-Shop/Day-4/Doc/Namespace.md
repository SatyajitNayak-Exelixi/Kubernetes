# 🐳 Kubernetes Namespace Guide

Namespaces in Kubernetes are used to **organize and isolate resources** within the same cluster. They allow multiple teams/projects to share the same cluster without interfering with each other.

---

## 🔹 Why Use Namespaces?

* Separation of resources between teams/projects.
* Apply different resource quotas & limits.
* Easier management of access control (RBAC).
* Avoid name conflicts for resources.

> ⚠️ Note: Some resources like `nodes` and `persistentVolumes` are **cluster-wide** and not bound to a namespace.

---

## 🔹 Common Namespace Commands

```bash
# List all namespaces
kubectl get namespaces

# Create a namespace
kubectl create namespace dev

# Describe a namespace
kubectl describe namespace dev

# Delete a namespace
kubectl delete namespace dev

# Run a pod in a specific namespace
kubectl run nginx --image=nginx -n dev

# Get resources from a specific namespace
kubectl get pods -n dev

# Switch default namespace for current context
kubectl config set-context --current --namespace=dev

# Verify current namespace
kubectl config view --minify | grep namespace:
```

---

## 🔹 Sample Namespace YAML

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: dev-namespace
  labels:
    environment: dev
```

Apply the namespace:

```bash
kubectl apply -f namespace.yaml
```

---

## 🔹 Example: Pod in a Namespace

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  namespace: dev-namespace   # Assign pod to namespace
  labels:
    app: nginx
spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80
```

Apply the Pod:

```bash
kubectl apply -f nginx-pod.yaml
```

