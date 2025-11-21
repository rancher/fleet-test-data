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
    │   │   ├── frontend-deployment.yaml
    │   │   ├── frontend-service.yaml
    │   │   ├── redis-master-deployment.yaml
    │   │   ├── redis-master-service.yaml
    │   │   ├── redis-slave-deployment.yaml
    │   │   └── redis-slave-service.yaml
    │   └── values.yaml
    └── true
        ├── Chart.yaml
        ├── fleet.yaml
        ├── README.md
        ├── templates
        │   ├── frontend-deployment.yaml
        │   ├── frontend-service.yaml
        │   ├── redis-master-deployment.yaml
        │   ├── redis-master-service.yaml
        │   ├── redis-slave-deployment.yaml
        │   └── redis-slave-service.yaml
        └── values.yaml
    ```
