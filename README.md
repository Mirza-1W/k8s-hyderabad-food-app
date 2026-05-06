# 🍛 Hyderabad Food App — Kubernetes Deployment

A production-style Kubernetes deployment built as part of my 
DevOps learning journey.

## 📦 What's Inside

| File | Purpose |
|------|---------|
| food-deployment.yaml | Deploys 3 nginx pods in hyderabad-food namespace |
| food-service.yaml | NodePort service exposing app on port 30005 |

## 🏗️ Architecture

Namespace: hyderabad-food
│
├── Deployment (3 replicas)
│     └── Pod x3 (nginx:1.25)
│           labels: app=food-app, env=production
│
└── Service (NodePort :30005)
selector: app=food-app

## 🚀 How to Deploy

```bash
# Create namespace
kubectl create namespace hyderabad-food

# Deploy app
kubectl apply -f food-deployment.yaml
kubectl apply -f food-service.yaml

# Access in browser
minikube service food-service -n hyderabad-food --url
```

## ✅ Features Demonstrated

- Namespace isolation
- Deployment with ReplicaSet self-healing
- NodePort Service with label selectors
- Resource requests and limits on all pods

## 🛠️ Tech Stack

- Kubernetes (Minikube)
- kubectl
- nginx:1.25
