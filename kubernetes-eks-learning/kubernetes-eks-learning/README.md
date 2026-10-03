# Kubernetes & Amazon EKS Learning

Hands-on Kubernetes and Amazon EKS learning repository covering core Kubernetes objects, Services, scaling, Metrics Server, and practical `kubectl` commands.

## 🎯 Learning Goals

- Understand Kubernetes core architecture and resources
- Deploy Java web applications on Amazon EKS
- Work with Pods and ReplicaSets
- Expose applications using ClusterIP, NodePort, and LoadBalancer
- Scale workloads up and down
- Monitor CPU and memory using Metrics Server
- Build a strong foundation for Deployments, HPA, Ingress, ConfigMaps, and Secrets

## 📚 Topics

| # | Topic | Status |
|---|---|---|
| 01 | Pods | ✅ Completed |
| 02 | ReplicaSets | ✅ Completed |
| 03 | Services | ✅ Completed |
| 04 | Scaling | ✅ Completed |
| 05 | Metrics Server / Metrics API | ✅ Completed |
| 06 | Deployments | 🔄 Learning |
| 07 | ConfigMaps | ⏳ Next |
| 08 | Secrets | ⏳ Planned |
| 09 | Readiness & Liveness Probes | ⏳ Planned |
| 10 | HPA | ⏳ Planned |
| 11 | Ingress | ⏳ Planned |

## 🏗️ Repository Structure

```text
kubernetes-eks-learning/
├── 01-pods/
│   └── pod-manifest.yml
├── 02-replicaset/
│   └── replicaset-manifest.yml
├── 03-services/
│   ├── clusterip-service.yml
│   ├── nodeport-service.yml
│   └── loadbalancer-service.yml
├── 04-scaling/
│   └── scaling-commands.md
├── 05-metrics-server/
│   └── metrics-server-notes.md
├── 06-deployments/
│   └── deployment-manifest.yml
├── commands/
│   └── kubectl-command-reference.md
└── README.md
```

## ☁️ Environment

The exercises are designed for:

- Amazon EKS
- AWS Region: `ap-south-1`
- Kubernetes
- `kubectl`
- `eksctl`
- Docker images hosted on Docker Hub

## 🐳 Application Images Used

The examples use Docker images from the author's Docker Hub account:

- `chaitanya4k/java-web-app`
- `chaitanya4k/spring-boot-docker-app`

## 🚀 Quick Start

Check the cluster:

```bash
kubectl get nodes
```

Check all resources:

```bash
kubectl get all -A
```

Create the practice namespace:

```bash
kubectl create namespace java-dev-ns
```

Apply a manifest:

```bash
kubectl apply -f 02-replicaset/replicaset-manifest.yml
```

Check Pods:

```bash
kubectl get pods -n java-dev-ns -o wide
```

Check ReplicaSet:

```bash
kubectl get rs -n java-dev-ns
```

Check Services:

```bash
kubectl get svc -n java-dev-ns
```

## 📊 Metrics Server

Install the current Metrics Server:

```bash
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```

Verify:

```bash
kubectl get pods -n kube-system | grep metrics-server
kubectl get apiservice | grep metrics
```

View node metrics:

```bash
kubectl top nodes
```

View Pod metrics:

```bash
kubectl top pods -A
```

## 📈 Scaling

Scale a ReplicaSet:

```bash
kubectl scale rs javawebrs --replicas=3 -n java-dev-ns
```

Scale it down:

```bash
kubectl scale rs javawebrs --replicas=2 -n java-dev-ns
```

Scale a Deployment:

```bash
kubectl scale deployment javaweb-deployment --replicas=3 -n java-dev-ns
```

## 🧹 Cleanup

For a practice namespace:

```bash
kubectl delete namespace java-dev-ns
```

If an EKS cluster is no longer needed:

```bash
eksctl delete cluster --name hk4-cluster --region ap-south-1 --wait
```

> ⚠️ AWS Cost Note: EKS worker nodes, LoadBalancer Services, NAT Gateways, EBS volumes, and other AWS resources can incur charges. Delete resources when the lab is finished.

## 🔐 Security

Never commit:

- AWS access keys
- AWS secret keys
- `.pem` files
- kubeconfig files containing sensitive credentials
- passwords
- application secrets

## 👨‍💻 Author

**Chaitanya K**

Java Developer | AWS | Docker | Kubernetes | DevOps

GitHub: [Chaitanya4K](https://github.com/Chaitanya4K)

---

This repository is a hands-on learning project and is continuously updated as new Kubernetes and AWS topics are practiced.
