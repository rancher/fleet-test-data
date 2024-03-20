# In this example, we are using the Fleet option keepResources: true/false.
# This option will ensure that deployed application will not be deleted
# after deleting a GitRepo.

This example will deploy the `nginx` application with 1 replica.
The app will be deployed to all available clusters in the `nginx-keep` namespace.
See [Target Matching](https://fleet.rancher.io/gitrepo-targets#target-matching)

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
    - clusterSelector: {}
```

