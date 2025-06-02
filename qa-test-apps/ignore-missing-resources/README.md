# In this example, we are using the `fleet.yaml` file option called `diff`
# Using `diff`, Fleet will ignore the missing resource and show `GitRepo`
# in `Active` state instead of `Modified` state for missing resource.

For more information about ignore-missing-resources, see ([Ignoring Entire Objects](https://fleet.rancher.io/bundle-diffs#ignoring-entire-objects))

To see GitRepo in
- Active state, use path: `qa-test-apps/ignore-missing-resources/with-diff`
- Modified state, user path: `qa-test-apps/ignore-missing-resources/without-diff`

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: ignore-missing-resources
  namespace: fleet-default
spec:
  repo: https://github.com/rancher/fleet-test-data/
  branch: master
  paths:
  - See above description for Path
  targets:
    - clusterSelector: {}
```
