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
```bash
k8s-voting-app/
├── k8s/                        # (Опционально) Ваши старые статические YAML
│   ├── redis-deployment.yaml
│   └── ...
├── voting-chart/               # Ваш основной Helm Chart
│   ├── Chart.yaml              # Метаданные чарта
│   ├── values.yaml             # Конфигурация (реплики, пароли, образы)
│   └── templates/              # Шаблоны манифестов
│       ├── _helpers.tpl        # (Оставьте, он полезен для имен)
│       ├── redis-deployment.yaml
│       ├── services.yaml       # Один файл для всех Service или по отдельности
│       └── ingress.yaml        # Настройка доступа через домен
├── .gitignore                  # Чтобы не пушить лишнее (например, .helmignore)
└── README.md                   # Лицо вашего проекта

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
```bash
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

"Project architecture includes a Helm Chart with Ingress routing. Successfully deployed on Minikube with automated service discovery."
