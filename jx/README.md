# Jenkins X 

## Installation

### With old JX Install: 

```shell script
jx install --provider openshift --static-jenkins --gitops
```

https://jenkins-x.io/docs/managing-jx/old/manage-via-gitops/

https://jenkins-x.io/commands/jx_install/

https://jenkins-x.io/docs/managing-jx/old/install-on-cluster/

### With newer JX Boot:

Checkout the [boot repository](https://github.com/baloise-incubator/jenkins-x-boot-config) and cd into it.

Run: 

```shell script
jx boot
```

https://jenkins-x.io/commands/jx_boot/

https://jenkins-x.io/docs/getting-started/setup/boot/