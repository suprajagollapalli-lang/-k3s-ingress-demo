# k3s Ingress Demo on AWS Free Tier

This repository demonstrates deploying two NGINX applications on a lightweight Kubernetes cluster (k3s) running on an AWS free-tier EC2 instance. The applications are exposed using the Traefik Ingress Controller with path-based routing.

---

## 🏗 Architecture

- **Cloud**: AWS EC2 (Free Tier)
- **OS**: Amazon Linux 2023
- **Kubernetes**: k3s (single-node)
- **Ingress Controller**: Traefik (default in k3s)
- **Applications**: Two NGINX apps
Internet
|
EC2 Public IP :80
|
Traefik Ingress Controller
|
├── /app1 → app1-service → nginx pod
└── /app2 → app2-service → nginx pod
---

## 🌐 Live Application URLs

The applications are accessible using the EC2 public IP:

- **App1** 👉 http://18.60.112.161/app1  
- **App2** 👉 http://18.60.112.161/app2  

> Note: These URLs work as long as the EC2 instance is running and the public IP remains unchanged.

---

## 📂 Kubernetes Manifests

| File | Description |
|-----|-------------|
| app1.yaml | Deployment & Service for App1 |
| app2.yaml | Deployment & Service for App2 |
| ingress.yaml | Ingress rules for /app1 and /app2 |
| strip-prefix.yaml | Traefik middleware to rewrite paths |

---

## 🌐 Routing

| URL | Backend |
|----|--------|
| /app1 | app1-service |
| /app2 | app2-service |

The Traefik middleware removes the path prefix before forwarding the request to the NGINX pod.

---

## 🚀 Deployment Steps

1. Install k3s on EC2
2. Deploy app1 and app2
3. Apply Traefik middleware
4. Apply Ingress configuration
5. Access apps using EC2 public IP

---

## ✅ Key Learnings

- Running Kubernetes on AWS free tier
- Using Traefik Ingress with k3s
- Path-based routing using Ingress
- Managing low-memory instances (swap configuration)
- Version-controlling Kubernetes manifests with Git

---

## 📝 Author

Created as a hands-on Kubernetes and DevOps learning project.
