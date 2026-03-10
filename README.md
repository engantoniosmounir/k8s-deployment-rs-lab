# Kubernetes Deployment & ReplicaSet Lab 🚀

This project demonstrates core Kubernetes workload management concepts using **ReplicaSets** and **Deployments**.
The lab focuses on **self-healing, scaling, rolling updates, and rollback mechanisms** in Kubernetes.

---

# 📌 Project Overview

In this lab we practice how Kubernetes manages containerized applications using:

* **ReplicaSet** to maintain a stable number of running Pods
* **Deployment** to manage ReplicaSets and provide application updates
* **Scaling** to increase or decrease application replicas
* **Rolling Updates** to update applications without downtime
* **Rollback** to restore previous versions when deployments fail

This lab simulates real tasks commonly required for **CKA (Certified Kubernetes Administrator)** preparation.

---

# 🧰 Technologies Used

* Kubernetes
* kubectl CLI
* YAML configuration files
* Nginx container image
* Minikube / Kubernetes Cluster

---

# 📂 Project Structure

```
k8s-deployment-rs-lab
│
├── frontend-rs.yaml
├── webapp-deploy.yaml
└── README.md
```

---

# ⚙️ ReplicaSet Configuration

ReplicaSet ensures that a specified number of Pod replicas are always running.

### Features Demonstrated

* Creating ReplicaSets
* Pod label selectors
* Self-healing mechanism

### Apply ReplicaSet

```
kubectl apply -f frontend-rs.yaml
```

### Verify

```
kubectl get rs
kubectl get pods -l app=frontend
```

---

# 🚀 Deployment Configuration

Deployment manages ReplicaSets and provides advanced application lifecycle management.

### Features Demonstrated

* Deployment creation
* Pod management
* Resource requests and limits
* Rolling updates
* Rollback capability

### Apply Deployment

```
kubectl apply -f webapp-deploy.yaml
```

### Verify Deployment

```
kubectl get deployment webapp-deploy
kubectl get all
```

---

# 📈 Scaling the Application

Scaling allows adjusting the number of application instances.

### Imperative Scaling

```
kubectl scale deployment webapp-deploy --replicas=5
```

### Verify

```
kubectl get deployment webapp-deploy
```

---

# 🔄 Rolling Update

Rolling updates allow updating container images without downtime.

### Update Image

```
kubectl set image deployment/webapp-deploy nginx=nginx:1.25
```

### Monitor Update

```
kubectl rollout status deployment/webapp-deploy
```

---

# ⏪ Rollback Deployment

If a deployment fails, Kubernetes allows reverting to the previous working version.

### Simulate Failed Deployment

```
kubectl set image deployment/webapp-deploy nginx=nginx:DOES-NOT-EXIST
```

### Rollback

```
kubectl rollout undo deployment/webapp-deploy
```

---

# 🔍 Testing Without Service

This lab demonstrates two ways to access Pods without creating a Service.

### Method 1 — Exec into Pod

```
kubectl exec -it <pod-name> -- curl localhost
```

### Method 2 — Port Forward

```
kubectl port-forward deployment/webapp-deploy 9090:80
```

Then access:

```
http://localhost:9090
```

---

# 🧠 Key Kubernetes Concepts Learned

* Kubernetes Pod lifecycle
* ReplicaSet architecture
* Deployment hierarchy
* Label selectors
* Self-healing containers
* Horizontal scaling
* Rolling updates
* Rollback mechanisms

---

# 📊 Deployment Architecture

```
Deployment
   │
   ▼
ReplicaSet
   │
   ▼
Pods
```

The **Deployment** manages ReplicaSets, while the **ReplicaSet** ensures the desired number of Pods are running.

---

# 🎯 Learning Outcome

After completing this lab, you should understand how Kubernetes:

* Maintains application availability
* Automatically replaces failed Pods
* Performs zero-downtime updates
* Enables safe rollback mechanisms

These skills are essential for **DevOps Engineers and Kubernetes Administrators**.

---

# 👨‍💻 Author

Antonios Mounir
Kubernetes Learning Lab
