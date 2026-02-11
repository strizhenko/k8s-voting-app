# Kubernetes Microservice Stack: Voting Application

This repository contains Kubernetes manifests for deploying a scalable, fault-tolerant microservices application. The project demonstrates advanced K8s concepts including workload orchestration, state management, and resource optimization.

## 🚀 Features & Architecture

- **High Availability:** Frontend is deployed with 3 replicas and automated self-healing.
- **Stateful Management:** PostgreSQL is managed via `StatefulSet` with persistent storage.
- **Service Discovery:** Internal communication between services using ClusterIP.
- **Traffic Management:** Exposed via NodePort for local testing (Minikube).
- **Health Monitoring:** Implemented Liveness and Readiness probes for zero-downtime.



## 🛠 Tech Stack

* **Platform:** Kubernetes (Minikube)
* **Workloads:** Deployments, StatefulSets
* **Storage:** PersistentVolumes (PV) & Claims (PVC)
* **Networking:** Services (NodePort, ClusterIP)
* **Config:** ConfigMaps & Secrets

## 📦 Deployment Instructions

1. **Start Minikube:**
   ```bash
   minikube start --driver=hyperv --cpus=4 --memory=6144
Create Namespace:

Bash
kubectl apply -f k8s/namespace.yaml
Deploy Configs & Secrets:

Bash
kubectl apply -f k8s/config-secrets.yaml
Deploy Application Stack:

Bash
kubectl apply -f k8s/
Access the App:
text
Bash
minikube service web-service -n voting-app
┌────────────┬─────────────┬─────────────┬─────────────────────────────┐
│ NAMESPACE  │    NAME     │ TARGET PORT │             URL             │
├────────────┼─────────────┼─────────────┼─────────────────────────────┤
│ voting-app │ web-service │ 80          │ http://172.23.245.184:30080 │
└────────────┴─────────────┴─────────────┴─────────────────────────────┘

📈 Future Improvements
[ ] Implement Ingress Controller with SSL/TLS.

[ ] Add Prometheus/Grafana monitoring stack.

[ ] Create a Helm Chart for automated releases.

Created as a demonstration of Cloud-Native Infrastructure skills.

"Access the application via minikube service web-service -n voting-app or through the configured NodePort (30080)."
