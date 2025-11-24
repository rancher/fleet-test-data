### In this example, Fleet will deploy bundle to cluster having same label from `fleet.yaml` file by overriding defined target in the `GitRepo`.

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
