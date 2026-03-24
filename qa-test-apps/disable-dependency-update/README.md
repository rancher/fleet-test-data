#### The following tree structure illustrates how the `disableDependencyUpdate` option is used with values `true or false` in `fleet.yaml`:

  - `disableDependencyUpdate: true` Fleet will not automatically download dependencies found in the Helm chart.

  - `disableDependencyUpdate: false`, Fleet will automatically download all dependencies referenced in the Helm chart.

    ```
    qa-test-apps/disable-dependency-update
    ├── false
    │   ├── Chart.yaml
    │   ├── fleet.yaml
    │   ├── README.md
    │   ├── templates
    │   │   └── configmap.yaml
    │   └── values.yaml
    ├── README.md
    └── true
        ├── Chart.yaml
        ├── fleet.yaml
        ├── README.md
        ├── templates
        │   └── configmap.yaml
        └── values.yaml
    ```

> [!WARNING]
> Some Helm chart dependencies may show a `Modified` state, which is detected in Helm v4. In these examples, resources in a modified state are excluded by disabling them in the `values.yaml` file.
