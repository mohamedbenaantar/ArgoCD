## Pre-requisites

1. Helm
2. Kubernetes Cluster

## Helm Installation v3

```sh
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```
## Create an "argo-cd" namespace within the cluster and switch to it

```sh
alias k=kubectl
k create ns argo-cd
k config set-context --current --namespace argo-cd
```
## Add argo Repo and install the package from it

```sh
helm repo add argo https://argoproj.github.io/argo-helm
helm repo list
helm install argocd argo/argo-cd -n argo-cd
```

## to see all installed components

```sh
k get all
```

## Note the Initial Admin password to access the Argo UI

```sh
 kubectl -n argo-cd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

## Edit the Service argocd to expose the Pod through Node port

```sh
k get svc
k edit svc argocd-server ##Change the type ClusterIP to NodePort 
```
## Get the error argoCd too many redirects

## Send --insecure arg for container of argocd-server Deployment

```sh
spec:
  containers:
  - command:
    - --insecure  ## Add the following command 
```

### You might need argocd CLI also to interact with argocd

```sh
curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
rm argocd-linux-amd64
argocd ## Check if it is installed successfully
```
