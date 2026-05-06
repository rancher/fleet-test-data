### In this example, we are testing if Helm charts can be pulled from OCI registries using the `oci://` URL format in the `chart` field of the `fleet.yaml` file.

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: test-helm-oci-chart-url
  namespace: fleet-default
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - qa-test-apps/helm-oci-tests/chart-oci-url
  targets:
    - clusterSelector: {}
```
