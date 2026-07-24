# Old Release Removal

The following tree structure illustrates how a bundle update that changes the Helm `releaseName` and `defaultNamespace` is used to verify old-release garbage collection (Fleet [issue #2169](https://github.com/rancher/fleet/issues/2169))

- `app-version-1` deploys into namespace `app-version-1` with Helm `releaseName: release1`.
- `app-version-2` deploys into namespace `app-version-2` with Helm `releaseName: release2`.
- Point a `GitRepo` at `app-version-1`, then update it to `app-version-2`: both the release name and namespace change.
- Fleet should remove the old `release1` release and create the new `release2` release. With a short `garbageCollectionInterval`, the old release is cleaned up promptly instead of after the default 15-minute delay.

    ```
    qa-test-apps/check-old-release-removal
    ├── README.md
    ├── app-version-1
    │   ├── configmap.yaml
    │   └── fleet.yaml
    └── app-version-2
        ├── configmap.yaml
        └── fleet.yaml
    ```

> [!NOTE]
> Fleet wraps every bundle in a Helm release, stored as a secret `sh.helm.release.v1.<releaseName>.v1` in the target namespace. After deploying `app-version-1` the secret `sh.helm.release.v1.release1.v1` exists in namespace `app-version-1`; after updating to `app-version-2` the secret `sh.helm.release.v1.release2.v1` appears in namespace `app-version-2` and the old `release1` secret is garbage-collected.
