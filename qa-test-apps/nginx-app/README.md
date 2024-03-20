# In this example, we are using fleet option keepResources: true/false.
# This option will ensure that deployed application will not be deleted
# after deleting GitRepo.

This example will deploy the `nginx` application with 1 replica.
The app will be deployed into the `nginx-keep` namespace.

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: keep-resources
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - qa-test-apps/nginx-app
  targetNamespace: keep-resources
  keepResources: true
  targets:
    - clusterSelector:
        matchExpressions:
          - key: provider.cattle.io
            operator: NotIn
            values:
              - harvester
```

