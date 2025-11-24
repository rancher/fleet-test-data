### In this example, the `disableDependencyUpdate: true` Fleet will not automatically download dependencies found in the Helm chart.

### Find more information about `disableDependencyUpdate` [click here](https://fleet.rancher.io/ref-fleet-yaml#chart-source)

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: test-disable-dependency-true-helm-chart
  namespace: fleet-default
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - qa-test-apps/disable-dependency-update/true
  targets:
    - clusterSelector: {}
```
