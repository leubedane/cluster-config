# cluster-config

In order to start with the configuration we need to get Argo CD setup first.

## Docs
The following parts of the documentation are useful for understanding our Argo CD configuration.

- for Role Base Access Control (RBAC) see [this page](https://argoproj.github.io/argo-cd/operator-manual/rbac/)
- for the High Availability (HA) configuration see [this page](https://argoproj.github.io/argo-cd/operator-manual/high_availability/)

## Argo CD Setup
Install into the Cluster by following the [Manual](https://argoproj.github.io/argo-cd/getting_started/#1-install-argo-cd)

You can also use the OC CLI and replace `kubectl` commands by `oc`.

For high availability use the following command instead of the normal install: 
`oc apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/ha/install.yaml`

We are dogfooding - therefore managing Argo CD using... Argo CD! 
See the [docs](https://argoproj.github.io/argo-cd/operator-manual/declarative-setup/#manage-argo-cd-using-argo-cd) for an explanation of these git repositories content.
Especially the [argocd](argocd) subfolder contains the configuration for argo CD itself.

## Create initial app
Once the Argo CD app is running, we need to create a first app (Argo CD iteself) - so it knows where this repository is located.

- hit the "NEW APPLICATION" button in the Argo CD UI
- select "EDIT AS YAML"
- Insert the following yaml content and hit "CREATE"

```yaml
project: default
source:
  repoURL: 'https://github.com/baloise-incubator/cluster-config.git'
  path: apps
  targetRevision: HEAD
  helm:
    valueFiles:
      - "values.yaml"
destination:
  server: 'https://kubernetes.default.svc'
  namespace: argocd
syncPolicy:
  automated:
    prune: true
    selfHeal: true
```

## Faster sync with webhook

For faster synchronization you should add a webhook to your git repository. See the [docs](https://argoproj.github.io/argo-cd/operator-manual/webhook/) for an example.


