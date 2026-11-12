#### The following tree structure illustrates how `${ }` templates are used in `namespaceLabels` and `namespaceAnnotations` in `fleet.yaml`:

  - `render`: `.ClusterName`, `.ClusterNamespace` and `.ClusterLabels.name` are rendered per target cluster into the namespace labels and annotations.

  - `disable-preprocess`: `helm.disablePreProcess: true` keeps the templates literal, so the API server rejects the namespace label.

  - `missing-label`: a template that refers to a cluster label which does not exist makes the bundle report a `namespaceLabels` render error.

    ```
    qa-test-apps/namespace-metadata-templating
    ├── disable-preprocess
    │   ├── config-chart
    │   │   ├── Chart.yaml
    │   │   ├── templates
    │   │   │   └── configmap.yaml
    │   │   └── values.yaml
    │   └── fleet.yaml
    ├── missing-label
    │   ├── config-chart
    │   │   └── ...
    │   └── fleet.yaml
    ├── README.md
    └── render
        ├── config-chart
        │   └── ...
        └── fleet.yaml
    ```

> [!NOTE]
> Templating in `namespaceLabels` / `namespaceAnnotations` requires Fleet v0.17.0 or later (Rancher 2.16+). On older versions the literal `${ }` reaches the namespace and the bundle ends in `ErrApplied`.
