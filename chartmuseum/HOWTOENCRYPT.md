```
kubeseal --cert ~/kubeseal/kubeseal.crt \
--namespace=chartmuseum -oyaml \
< chartmuseum-secret.yaml.ignore > chartmuseum-sealed-secret.yaml
```