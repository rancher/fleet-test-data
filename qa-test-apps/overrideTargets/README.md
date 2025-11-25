### In this example, Fleet will deploy the bundle to clusters that match the label specified in the `fleet.yaml` file, overriding any targets defined in the `GitRepo`.

This example will deploy the `nginx` application with 1 replica.
The `nginx-override` app will be deployed to cluster(s) which matches label from `fleet.yaml` file.
See [overrideTargets](https://fleet.rancher.io/ref-fleet-yaml#general-bundle-configuration)

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: test-fleet-override-targets
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - qa-test-apps/overrideTargets
  targets:
    - clusterSelector: {}
```
