### The following tree structure illustrates how the `doNotDeploy` option is used with values `true or false` in `fleet.yaml`:

  - `doNotDeploy: true`: When set to `true`, `Fleet` skips deploying resources to clusters that match the specified labels in the `targetCustomizations` section.

  - `doNotDeploy: false`: When set to `false`, `Fleet` deploys resources to all clusters, regardless of their labels.
    ```
    qa-test-apps/do-not-deploy
    ├── false
    │   ├── fleet.yaml
    │   ├── nginx.yaml
    │   └── README.md
    └── true
        ├── fleet.yaml
        ├── nginx.yaml
        └── README.md
    ```
