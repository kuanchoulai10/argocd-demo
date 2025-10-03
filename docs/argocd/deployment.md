# ArgoCD Deployment


[Getting Started](https://argo-cd.readthedocs.io/en/stable/getting_started/)


```bash
export ARGOCD_VERSION=v3.1.7
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/$ARGOCD_VERSION/manifests/install.yaml
```

```bash
argocd login --core --insecure
```

```bash
argocd app create guestbook \
  --repo https://github.com/argoproj/argocd-example-apps.git \
  --path guestbook \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace default
```

```bash
argocd app get guestbook
```

??? info "Result"

    ```
    argocd app get guestbook
    Name:               argocd/guestbook
    Project:            default
    Server:             https://kubernetes.default.svc
    Namespace:          default
    URL:                http://localhost:63390/applications/guestbook
    Source:
    - Repo:             https://github.com/argoproj/argocd-example-apps.git
    Target:           
    Path:               guestbook
    SyncWindow:         Sync Allowed
    Sync Policy:        Manual
    Sync Status:        Synced to  (0d521c6)
    Health Status:      Healthy

    GROUP  KIND        NAMESPACE  NAME          STATUS  HEALTH   HOOK  MESSAGE
           Service     default    guestbook-ui  Synced  Healthy        service/guestbook-ui created
    apps   Deployment  default    guestbook-ui  Synced  Healthy        deployment.apps/guestbook-ui created
    ```

```bash
argocd app sync guestbook
```


```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

```
https://localhost:8080
```

```
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