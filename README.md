# argocd

## Getting Started

### Install Argo CD

```bash
kubectl create ns argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### Instal Argo CD CLI

```bash
brew install argocd
```

### Expose Argo CD in Local via `port-forwarding`

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

> expose argocd to port :8080, access in http://localhost:8080

### Login via CLI

```bash
argocd admin initial-password -n argocd
```

### Update password & remove initial password

```bash
argocd login localhost:8080
```

```bash
argocd account update-password
```
> Remove secret `argocd-initial-admin-secret`

```bash
kubectl delete secret/argocd-initial-admin-secret
```
### Add Ingress

> First we need to edit deployment/argocd-server and add flag `--insecure` to the argocd-server command. Then edit svc/argocd-server and remove port :443

```bash
kubectl apply -f ingress.yaml
```

