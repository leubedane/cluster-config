https://github.com/chartmuseum/helm-push
```
helm plugin install https://github.com/chartmuseum/helm-push
helm repo add baloise-incubator https://charts.baloise.dev
helm push <chart>/ baloise-incubator --username=<user> --password=<password>
```