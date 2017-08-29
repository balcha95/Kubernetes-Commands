# Kubernetes Commands

Helper setup to edit .yaml files with Vim:

- [VIM Setup for Yaml files](#vim-setup-for-yaml-files)

List of general purpose commands for Kubernetes management:

- [PODS](#pods)
- [Create Deployments](#create-deployments)
- [Scaling PODs](#scaling-pods)
- [POD Upgrade / History](#pod-upgrade-and-history)
- [Services](#services)

## VIM Setup for Yaml files

Plase the following lines in ~/.vimrc:

```
autocmd FileType yaml setlocal ts=2 sts=2 sw=2 expandtab
filetype plugin indent on
autocmd FileType yaml setl indentkeys-=<:>

```

## PODS

```
$ kubectl get pods
$ kubectl get pods --all-namespaces
$ kubectl get pod monkey -o wide
$ kubectl get pod monkey -o yaml
```

## Create Deployments

Create single deployment

```
$ kubectl run monkey --image=monkey --record
```

## Scaling PODs

```bash
$ kubectl scale deployment/POD_NAME --replicas=N
```

## POD Upgrade and history

#### List history of deployments

```
$ kubectl rollout history deployment/DEPLOYMENT_NAME
```

#### Jump to specific revision

```
$ kubectl rollout undo deployment/DEPLOYMENT_NAME --to-revision=N
```

## Services

List services

```
$ kubectl get services
```

Expose PODs as services (creates endpoints)

```
$ kubectl expose deployment/monkey --port=2001 --type=NodePort
```
