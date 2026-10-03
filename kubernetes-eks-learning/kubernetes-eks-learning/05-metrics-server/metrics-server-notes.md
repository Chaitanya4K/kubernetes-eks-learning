# Kubernetes Metrics Server / Metrics API

Metrics Server collects CPU and memory resource metrics from Kubernetes nodes and Pods and exposes them through the Metrics API.

## Install Metrics Server

```bash
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```

## Verify the Deployment

```bash
kubectl get deployment metrics-server -n kube-system
```

## Check the Pod

```bash
kubectl get pods -n kube-system | grep metrics-server
```

Expected state:

```text
1/1 Running
```

## Verify Metrics API

```bash
kubectl get apiservice | grep metrics
```

## View Node Metrics

```bash
kubectl top nodes
```

## View Pod Metrics

```bash
kubectl top pods -A
```

## Important

Metrics Server is intended primarily for Kubernetes resource metrics and autoscaling use cases. It is not a replacement for a full monitoring stack such as Prometheus/Grafana.

## Troubleshooting

If `kubectl top` does not work immediately, wait for Metrics Server to become ready and try again:

```bash
kubectl get pods -n kube-system
kubectl describe pod -n kube-system -l k8s-app=metrics-server
kubectl logs -n kube-system deployment/metrics-server
```
