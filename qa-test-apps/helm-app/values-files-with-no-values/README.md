# Helm Example

This example will deploy the `redis` application deployment with custom values from file using `valuesFiles` in `fleet.yaml`.
The app will be deployed into the `fleet-helm-example` namespace.

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: helm
  namespace: fleet-local
spec:
  repo: https://github.com/rancher/fleet-test-data
  paths:
  -   - qa-test-apps/helm-app/values-files-with-no-values
```
