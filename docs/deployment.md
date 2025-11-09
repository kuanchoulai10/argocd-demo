# Argo CD Deployment


[Getting Started](https://argo-cd.readthedocs.io/en/stable/getting_started/)


```bash
export ARGOCD_VERSION=v3.1.7
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/$ARGOCD_VERSION/manifests/install.yaml
```

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

```
https://localhost:8080
```

```bash
argocd admin initial-password -n argocd
```

## Multi-region multi-environment deployment

- [Kustomize](https://argo-cd.readthedocs.io/en/stable/user-guide/kustomize/)
- [Kustomizing Helm charts](https://argo-cd.readthedocs.io/en/stable/user-guide/kustomize/#kustomizing-helm-charts)
- [Cluster Management](https://argo-cd.readthedocs.io/en/stable/operator-manual/cluster-management/)
- [Cluster Bootstrapping](https://argo-cd.readthedocs.io/en/stable/operator-manual/cluster-bootstrapping/)
- [Cluster | Declarative Setup](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/#clusters)
- [Helm | Declarative Setup](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/#helm)
- [Introduction to ApplicationSet controller](https://argo-cd.readthedocs.io/en/stable/operator-manual/applicationset/)