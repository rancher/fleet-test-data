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
> The `Service` is what makes this bundle useful — do not "simplify" it away.
> The bug leaked `helm.sh/resource-policy: keep` onto every resource processed
> *after* the first CRD. Helm sorts manifests by install order before Fleet's
> post-renderer runs, and `CustomResourceDefinition` sorts **after** `ConfigMap`
> but **before** `Service`. A bundle of CRD + ConfigMap alone would therefore
> pass even on an affected build. The `ConfigMap` is kept deliberately as the
> other side of that boundary.

> [!NOTE]
> Each directory declares a different CRD name and `defaultNamespace`. Under
> `default` the CRD outlives its `GitRepo` by design — that is what `keep` means —
> so sharing a name across the two bundles would break Helm release ownership.
> Remove it explicitly with
> `kubectl delete crd resourcepolicykeeps.qa.fleet.cattle.io` when cleaning up.
