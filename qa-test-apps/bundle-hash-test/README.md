### In this example, we are checking bundle hash mismatch.

  ```bash
  qa-test-apps/bundle-hash-test
  ├── Chart.yaml
  ├── README.md
  ├── templates
  │   └── configmap.yaml
  └── values.yaml
  ```
### See issue for more details: https://github.com/rancher/fleet/issues/3807#issuecomment-3376900740 

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: test-bundle-hash-mistmatch
  namespace: fleet-default
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - qa-test-apps/bundle-hash-test
  targets:
    - clusterSelector: {}
```
