# GC of Long Bundle Names

The following tree structure illustrates how a bundle whose name exceeds Helm's 53-character release-name limit is used to verify that the agent's garbage collector leaves a valid Helm release alone (Fleet [issue #5261](https://github.com/rancher/fleet/issues/5261), backport [#5399](https://github.com/rancher/fleet/issues/5399))

- `fleet.yaml` sets `name: repro-bundle-name-that-exceeds-the-53-char-helm-limit-x` (55 characters) and deliberately does **not** set `helm.releaseName`, so Fleet derives the release name itself.
- Fleet truncates a name longer than 53 characters to `<first 47 characters>-<md5(name)[:5]>`, so the Helm release is installed as `repro-bundle-name-that-exceeds-the-53-char-helm-98fdb`.
- Before the fix the garbage collector compared the untruncated `BundleDeployment` name against the truncated name Helm had actually stored, concluded the release was orphaned and ran `helm uninstall` on it every collection cycle.
- Point a `GitRepo` at this path with a short `garbageCollectionInterval` and the release must survive untouched.

    ```
    qa-test-apps/gc-long-bundle-name
    ├── README.md
    ├── configmap.yaml
    └── fleet.yaml
    ```

> [!NOTE]
> A green result is vacuous on its own, because the agent only logs and acts when it decides to delete something: a collector that never ran looks identical to a collector that ran and correctly did nothing. Pair this bundle with a control that genuinely orphans a release — for example `qa-test-apps/check-old-release-removal`, where repointing a `GitRepo` from `app-version-1` to `app-version-2` changes the release name and the old `release1` release must disappear.

> [!NOTE]
> A `helm uninstall` by the garbage collector deletes the deployed resources, after which Fleet redeploys them. The presence of `gc-long-bundle-name-config` therefore does not by itself prove the release survived — compare its `metadata.uid` before and after the collection window instead.
