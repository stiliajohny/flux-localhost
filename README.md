# Flux Configuration with k3d-local Cluster

This repository contains the necessary configurations for bootstrapping a Kubernetes cluster managed by Flux in a GitOps fashion. This particular setup is tailored for a k3d-local cluster.

## Table of Contents

- [Flux Configuration with k3d-local Cluster](#flux-configuration-with-k3d-local-cluster)
  - [Table of Contents](#table-of-contents)
  - [Prerequisites](#prerequisites)
  - [Getting Started](#getting-started)
    - [Clone the Repository](#clone-the-repository)
    - [Bootstrap Flux](#bootstrap-flux)
  - [Folder Structure](#folder-structure)
  - [File Descriptions](#file-descriptions)
  - [Adding New Namespaces or Resources](#adding-new-namespaces-or-resources)

## Prerequisites

- Kubernetes Cluster
- `flux` CLI
- `kubectl` CLI
- `git`

## Getting Started

### Clone the Repository

To start, clone this repository to your local machine:

```bash
git clone github.com:stiliajohny/flux-localhost.git
```

### Bootstrap Flux

Navigate to the root directory of the repository and execute the following command to bootstrap Flux to your cluster:

```bash
flux bootstrap git \
 --url=ssh://git@ithub.com:stiliajohny/flux-localhost \
 --branch=master \
 --path=./cluster/k3d-local
```

## Folder Structure

The repository has the following folder structure:

```bash
.
└── cluster
    └── k3d-local
        ├── flux-system
        │ ├── gotk-components.yaml
        │ ├── gotk-sync.yaml
        │ └── kustomization.yaml
        └── monitoring
            ├── kustomization.yaml
            └── namespace.yaml
```

## File Descriptions

- `gotk-components.yaml`: Contains the Flux custom resource definitions (CRDs) and controllers.
- `gotk-sync.yaml`: Configures the synchronization settings between your Git repository and the cluster.
- `kustomization.yaml` (in `flux-system`): Orchestrates the resources in the `flux-system` directory.
- `kustomization.yaml` (in `monitoring`): Orchestrates the resources in the `monitoring` directory.
- `namespace.yaml`: Defines the monitoring namespace.

## Adding New Namespaces or Resources

1. Create a new directory under `k3d-local` for the namespace.
2. Add a `kustomization.yaml` and the respective resource YAML files in the new directory.
3. Update the `kustomization.yaml` in `flux-system` to include the new directory under `resources:`.

For more information on how to structure new resources, refer to the existing `monitoring` directory as an example.
