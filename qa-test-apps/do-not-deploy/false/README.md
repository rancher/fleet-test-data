### In this example, resources are deployed to all clusters because the `doNotDeploy` option is set to `false` under `targetCustomizations`.

### Find more information about `doNotDeploy` [click here](https://fleet.rancher.io/ref-fleet-yaml#targeting-and-customization)

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: test-resources-deployed-to-all-clusters
  namespace: fleet-default
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - qa-test-apps/do-not-deploy/false
  targets:
    - clusterSelector: {}
```
