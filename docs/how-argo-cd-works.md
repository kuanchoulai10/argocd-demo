---
tags:
  - Argo CD
  - GitOps
---
# How Argo CD Works

## System Components

![](https://argo-cd.readthedocs.io/en/stable/assets/argocd_architecture.png){width=600}
/// caption
[ArgoCD Architecture](https://argo-cd.readthedocs.io/en/stable/#architecture)
///

### API Server

: *The API server is a gRPC/REST server which exposes the API consumed by the Web UI, CLI, and CI/CD systems.*

### Repository Server

: *The repository server is an internal service which maintains a local cache of the Git repository holding the application manifests.*

### Application Controller

: *The application controller is a Kubernetes controller which continuously monitors running applications and compares the current, live state against the desired target state (as specified in the repo)*

### Application Set Controller

### [Dex Server](https://argo-cd.readthedocs.io/en/stable/operator-manual/user-management/#dex)

### [Notifications Controller](https://argo-cd.readthedocs.io/en/stable/operator-manual/notifications/)

### Redis

## Sync Phases and Waves

![](https://argo-cd.readthedocs.io/en/stable/user-guide/how_phases_work.png)
/// caption
The Sync Process
///

| Hook       | Description                                                                                                                  |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------- |
| PreSync    | Executes prior to the application of the manifests.                                                                          |
| Sync       | Executes after all PreSync hooks completed and were successful, at the same time as the application of the manifests.        |
| Skip       | Indicates to Argo CD to skip the application of the manifest.                                                                |
| PostSync   | Executes after all Sync hooks completed and were successful, a successful application, and all resources in a Healthy state. |
| SyncFail   | Executes when the sync operation fails.                                                                                      |
| PostDelete | Executes after all Application resources are deleted. *Available starting in v2.10*.                                         |

