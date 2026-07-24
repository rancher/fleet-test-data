# Namespace Labels and Annotations

The following tree structure illustrates how `namespaceLabels` and `namespaceAnnotations` in `fleet.yaml` are applied to the namespace Fleet creates for a bundle (Fleet [issue #1553](https://github.com/rancher/fleet/issues/1553)).

- `fleet.yaml` sets `defaultNamespace: my-labeled-namespace` and configures `namespaceLabels` (`env: test`) and `namespaceAnnotations` (`pod: deny`).
- When the bundle is deployed, Fleet creates `my-labeled-namespace` with those labels and annotations applied to it.

    ```text
    qa-test-apps/namespace-labels-annotations
    ├── README.md
    ├── configmap.yaml
    └── fleet.yaml
    ```

> [!NOTE]
> `namespaceLabels` and `namespaceAnnotations` apply only to the namespace that Fleet creates (the `defaultNamespace` / `targetNamespace`). They are not applied to namespaces defined as resources inside the bundle. This is commonly used to add Pod Security Admission labels to bundle namespaces.
