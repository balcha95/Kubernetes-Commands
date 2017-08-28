# Kubernetes Commands

List of general purpose commands for Kubernetes management:

## PODS

```
$ kubectl get pods
$ kubectl get pods --all-namespaces
$ kubectl get pod fluent-bit -o wide
$ kubectl get pod fluent-bit -o yaml
```

## Scaling PODs

```bash
$ kubectl scale deployment/POD_NAME --replicas=N
```

- $ kubectl scale
- $ kubectl label
- $ kubectl get 
  - pods
  - deployments
  - rs | replicasets
  - logs
  - run 

