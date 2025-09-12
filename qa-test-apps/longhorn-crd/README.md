# In this example, we are checking after installation of longhorn-crd,
# bundle is not in `Modified` state instead it is in `Active` state.
# See issue for more details: https://github.com/rancher/fleet/issues/2521

This example will deploy the `longhorn CRD's`.
See [Target Matching](https://fleet.rancher.io/gitrepo-targets#target-matching)

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: test-longhorn-crd-gitrepo-status
  namespace: fleet-default
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - qa-test-apps/longhorn-crd
  targets:
    - clusterSelector: {}
```

