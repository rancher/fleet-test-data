### In this example, we are checking if path contains some resources 
### not to be installed/deployed from `.fleetignore` file.
- Below tree structure illustrates files to be ignored and not to ignore.
  ```bash
  qa-test-apps/fleet-ignore-test
  ├── configmap-to-be-ignored.yaml
  ├── folder-to-be-ignored
  │   └── ignored_config_map.yaml
  ├── nginx
  │   └── nginx-not-to-be-ignored.yaml
  └── README.md
  ```
### See issue for more details: https://github.com/rancher/fleet/issues/583 
### Find more information about `.fleetignore` [click here](https://fleet.rancher.io/gitrepo-content#excluding-files-and-directories-from-bundles)

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: test-resource-from-fleet-ignore
  namespace: fleet-default
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - qa-test-apps/fleet-ignore-test
  targets:
    - clusterSelector: {}
```
