# ArgoCD Deployment

```bash
export ARGOCD_VERSION=v3.1.7
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/$ARGOCD_VERSION/manifests/install.yaml
```

