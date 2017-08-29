# Kubernetes Commands

Helper setup to edit .yaml files with Vim:

- [VIM Setup for Yaml files](#vim-setup-for-yaml-files)

List of general purpose commands for Kubernetes management:

- [PODS](#pods)
- [Create Deployments](#create-deployments)
- [Scaling PODs](#scaling-pods)
- [POD Upgrade / History](#pod-upgrade-and-history)
- [Services](#services)
- [Volumes](#volumes)
- [Secrets](#secrets)
- [ConfigMaps](#configmaps)

## VIM Setup for Yaml files

Put the following lines in ~/.vimrc:

```
" Yaml file handling
autocmd FileType yaml setlocal ts=2 sts=2 sw=2 expandtab
filetype plugin indent on
autocmd FileType yaml setl indentkeys-=<:>

" Copy paste with ctr+c, ctr+v, etc
:behave mswin
:set clipboard=unnamedplus
:smap <Del> <C-g>"_d
:smap <C-c> <C-g>y
:smap <C-x> <C-g>x
:imap <C-v> <Esc>pi
:smap <C-v> <C-g>p
:smap <Tab> <C-g>1> 
:smap <S-Tab> <C-g>1<
```

Keyboard hints:

- ctrl + f: auto indent line (requires INSERT mode)

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

## Volumes

Lits Persistent Volumes and Persistent Volumes Claims:

```
$ kubectl get pv
$ kubectl get pvc
```

## Secrets

```
$ kubectl get secrets
$ kubectl create secret generic --help
$ kubectl create secret generic mysql --from-literal=password=root
$ kubectl get secrets mysql -o yaml
```
## ConfigMaps

```
$ kubectl create configmap foobar --from-file=config.js
$ kubectl get configmap foobar -o yaml
```

## DNS

List DNS-PODs:

```
$ kubectl get pods --all-namespaces |grep dns
```

Check DNS for pod nginx (assuming a busybox POD/container is running)

```
$ kubectl exec -ti busybox -- nslookup nginx
```
