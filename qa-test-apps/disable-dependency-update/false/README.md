### In this example, the `disableDependencyUpdate: false`, Fleet will automatically download all dependencies referenced in the Helm chart.

### Find more information about `disableDependencyUpdate` [click here](https://fleet.rancher.io/ref-fleet-yaml#chart-source)

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: test-disable-dependency-false-helm-chart
  namespace: fleet-default
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - qa-test-apps/disable-dependency-update/false
  targets:
    - clusterSelector: {}
```
