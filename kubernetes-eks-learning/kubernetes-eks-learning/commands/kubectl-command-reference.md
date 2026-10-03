# Kubernetes Command Reference

## Cluster

```bash
kubectl cluster-info
kubectl get nodes
kubectl get nodes -o wide
```

## Namespaces

```bash
kubectl get namespaces
kubectl create namespace java-dev-ns
kubectl get namespace java-dev-ns
kubectl delete namespace java-dev-ns
```

## Pods

```bash
kubectl get pods
kubectl get pods -n java-dev-ns
kubectl get pods -n java-dev-ns -o wide
kubectl describe pod <pod-name> -n java-dev-ns
kubectl logs <pod-name> -n java-dev-ns
kubectl delete pod <pod-name> -n java-dev-ns
```

## ReplicaSets

```bash
kubectl get rs -n java-dev-ns
kubectl describe rs javawebrs -n java-dev-ns
kubectl scale rs javawebrs --replicas=3 -n java-dev-ns
kubectl scale rs javawebrs --replicas=2 -n java-dev-ns
kubectl delete rs javawebrs -n java-dev-ns
```

## Deployments

```bash
kubectl get deployments -n java-dev-ns
kubectl describe deployment javaweb-deployment -n java-dev-ns
kubectl scale deployment javaweb-deployment --replicas=3 -n java-dev-ns
kubectl rollout status deployment/javaweb-deployment -n java-dev-ns
kubectl rollout history deployment/javaweb-deployment -n java-dev-ns
```

## Services

```bash
kubectl get svc -n java-dev-ns
kubectl describe svc javawebappsvc -n java-dev-ns
```

## Apply / Delete YAML

```bash
kubectl apply -f <file>.yml
kubectl delete -f <file>.yml
```

## Metrics

```bash
kubectl top nodes
kubectl top pods -A
```

## All Resources

```bash
kubectl get all -n java-dev-ns
kubectl get all -A
```

## EKS

```bash
aws eks list-clusters --region ap-south-1
aws eks describe-cluster --name hk4-cluster --region ap-south-1
eksctl get cluster --region ap-south-1
```

## EKS Cleanup

```bash
eksctl delete cluster --name hk4-cluster --region ap-south-1 --wait
```

> Always verify AWS resources after cleanup, especially Load Balancers, NAT Gateways, EBS volumes, and running EC2 instances.
