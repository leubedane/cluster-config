```
kubeseal --cert https://raw.githubusercontent.com/baloise-incubator/getting-started/master/sealed-secrets/kubeseal.crt \
--namespace=guacamole \
< mysql-secret.yaml.ignore > mysql-sealed-secret.json
```