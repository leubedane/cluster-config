# Argo CD 

## Setup
Install into the Cluster by following the [Manual](https://argoproj.github.io/argo-cd/getting_started/#1-install-argo-cd)

You can also the OC CLI and replace `kubectl` commands by `oc`.

For high availability use the following command instead of the normal install: 
`oc apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/ha/install.yaml`

We are dogfooding - therefore managing Argo CD using... Argo CD! 
See the [docs](https://argoproj.github.io/argo-cd/operator-manual/declarative-setup/#manage-argo-cd-using-argo-cd) for an explanation of this folders content.
