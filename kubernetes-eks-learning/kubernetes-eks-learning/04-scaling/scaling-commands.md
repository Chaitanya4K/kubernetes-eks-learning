# Scaling Practice

## Check current ReplicaSet

```bash
kubectl get rs -n java-dev-ns
kubectl get pods -n java-dev-ns
```

## Scale ReplicaSet from 2 to 3

```bash
kubectl scale rs javawebrs --replicas=3 -n java-dev-ns
```

## Scale ReplicaSet from 3 to 2

```bash
kubectl scale rs javawebrs --replicas=2 -n java-dev-ns
```

## Delete a Pod

```bash
kubectl delete pod <pod-name> -n java-dev-ns
```

The ReplicaSet automatically creates a replacement Pod to maintain the desired replica count.

## Verify

```bash
kubectl get rs -n java-dev-ns
kubectl get pods -n java-dev-ns
```
