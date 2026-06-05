# In this example, we will deploy the `nginx` application with delayed readiness. The app will be deployed to all available clusters in the `nginx-delayed-readiness` namespace

## This nginx-delayed-readiness deployment is used to check the GitRepo's `notReady` state

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: test-gitrepo-not-ready-state
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - qa-test-apps/nginx-app-with-delayed-readiness
  targets:
    - clusterSelector: {}
```
