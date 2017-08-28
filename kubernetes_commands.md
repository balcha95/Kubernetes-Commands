# Kubernetes Commands

List of general purpose commands for Kubernetes management:

- [PODS](#pods)

## PODS

```
$ kubectl get pods
$ kubectl get pods --all-namespaces
$ kubectl get pod fluent-bit -o wide
$ kubectl get pod fluent-bit -o yaml
```

## Create Deployments

Create single deployment

```
$ kubectl run ghost --image=ghost --record
```

## Scaling PODs

```bash
$ kubectl scale deployment/POD_NAME --replicas=N
```

## POD Upgrade/history

#### List history of deployments

```
$ kubectl rollout history deployment/DEPLOYMENT_NAME
```

#### Jump to specific revision

```
$ kubectl rollout undo deployment/DEPLOYMENT_NAME --to-revision=N
```
- $ kubectl scale
- $ kubectl label
- $ kubectl get 
  - pods
  - deployments
  - rs | replicasets
  - logs
  - run 

