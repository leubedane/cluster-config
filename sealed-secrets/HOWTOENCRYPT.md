# sealed-secrets

Create kubeseal directory
```
mkdir ~/kubeseal
```

## Fetch certificate
```
kubeseal --controller-name=sealed-secrets \
--controller-namespace=sealed-secrets \
--fetch-cert >  ~/kubeseal/kubeseal.crt
```

## Create and encrypt generic secret
```
kubectl create secret generic secret-example \
--from-literal=password=$ECRET! \
--dry-run \
-oyaml > secret-example.json
```

```
kubeseal --cert ~/kubeseal/kubeseal.crt \
--namespace=<target-namespace> -oyaml \
< secret-example.json > namespaced-sealed-secret-example.json
```

## Create and encrypt pull secret
```
kubectl create secret docker-registry harbor-pull-secret \
--docker-server=harbor.apps.baloise.dev \
--docker-username=admin \
--docker-password=Harbor12345 \
--dry-run -oyaml > pull-secret-example.json
```
```
kubeseal --cert ~/kubeseal/kubeseal.crt \
--namespace=<target-namespace> -oyaml \
< pull-secret-example.json > sealed-pull-secret-example.json
```
### Add pull secret to ServiceAccount
```
kubectl patch serviceaccount default -p '{"imagePullSecrets": [{"name": "harbor-pull-secret"}]}'
```
