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
flux bootstrap github \
--owner=stiliajohny \
--repository=flux-localhost \
--branch=master \
--path=./cluster/k3d-local \
--token-auth
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
