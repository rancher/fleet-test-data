## Helm App examples

Below table illustrates `oci://` repo used via `chart` and `repo` fields in `fleet.yaml` file.

qa-test-apps/helm-oci-tests
├── chart-oci-url
│   ├── fleet.yaml
│   └── README.md
├── README.md
└── repo-oci-url
    ├── fleet.yaml
    └── README.md

| Example | Description |
| ------------- | ------------ |
| [repo-oci-url](qa-test-apps/helm-oci-tests/repo-oci-url) | An example using Helm with `oci://` URL format in the `repo` field of the `fleet.yaml` file |
| [chart-oci-url](qa-test-apps/helm-oci-tests/chart-oci-url) | An example using Helm with `oci://` URL format in the `chart` field of the `fleet.yaml` file |

_Note: README is present for each examples in respective folders.