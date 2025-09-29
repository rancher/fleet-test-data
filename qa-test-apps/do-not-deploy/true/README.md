### In this example, the `doNotDeploy: true` option is specified under `targetCustomizations`. This tells `Fleet` to skip deploying the resources to any clusters that match the given `label` selector.

### Find more information about `doNotDeploy` [click here](https://fleet.rancher.io/ref-fleet-yaml#targeting-and-customization)

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: test-resources-deployed-to-clusters-which-has-label
  namespace: fleet-default
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - qa-test-apps/do-not-deploy/true
  targets:
    - clusterSelector: {}
```
