# The following tree structure illustrates how `deleteCRDResources` in `fleet.yaml` controls the `helm.sh/resource-policy: keep` annotation

- `deleteCRDResources` unset (defaults to `false`) — Fleet annotates **only the CRDs** with `helm.sh/resource-policy: keep`.

- `deleteCRDResources: true` — Fleet annotates **nothing**; the CRDs are removed along with the rest of the bundle.

    ```yaml
    qa-test-apps/helm-resource-policy
    ├── default
    │   ├── configmap.yaml
    │   ├── crd.yaml
    │   ├── fleet.yaml
    │   └── service.yaml
    ├── delete-crd-resources
    │   ├── configmap.yaml
    │   ├── crd.yaml
    │   ├── fleet.yaml
    │   └── service.yaml
    └── README.md
    ```

See issue for more details: https://github.com/rancher/fleet/issues/2716

> [!IMPORTANT]
> `default` is the regression check; do not "simplify" the `Service` away.
> The bug leaked the annotation onto every resource processed *after* the first
> CRD. Fleet packages these plain YAML files into a Helm chart, and Helm sorts
> the manifests **by kind** before Fleet's post-renderer sees them:
> `ConfigMap` → `CustomResourceDefinition` → `Service`. So the `Service` is the
> resource that used to inherit the annotation and the `ConfigMap` is the control
> on the other side. Renaming the files is harmless, but replacing the `Service`
> with an early-sorting kind such as `Secret` or `ServiceAccount` would silently
> stop this bundle from catching the regression.

> [!NOTE]
> `delete-crd-resources` covers the flag's behaviour, not the bug — with
> `deleteCRDResources: true` the affected code path never runs, so the result is
> the same before and after the fix.

> [!NOTE]
> Each directory uses a different CRD name and `defaultNamespace`. Under `default`
> the CRD outlives its `GitRepo` by design — that is what `keep` means — so a
> shared name would break Helm release ownership. Clean up with
> `kubectl delete crd resourcepolicykeeps.qa.fleet.cattle.io`.
