# Infrastructure as Code

This repository contains an Infrastructure as Code (IaC) implementation for a modern Kubernetes platform using Talos OS and Flux. This is for my own homelab, and not an example or how-to.

## Overview

This implementation leverages:

- **[Kubernetes](https://kubernetes.io/)**: Container orchestration platform for automating deployment, scaling, and management of containerized applications
- **[Flux](https://fluxcd.io/)**: GitOps toolkit for keeping Kubernetes clusters in sync with configuration sources


## Architecture

The infrastructure is managed using GitOps principles, where:

1. **Kubernetes** serves as the orchestration platform for containerized workloads
2. **Flux** continuously reconciles the desired state (defined in Git) with the actual cluster state

## Disclaimer

**USE AT YOUR OWN RISK**

This repository is a personal homelab project and is provided "as is" without warranty of any kind, express or implied. The configurations and code contained herein are specific to my environment and may not be suitable for your use case.

- ⚠️ No warranty or guarantee of functionality
- ⚠️ Not intended as production-ready code
- ⚠️ Use at your own risk and discretion
- ⚠️ Always review and test configurations before applying to your infrastructure


The author(s) assume no responsibility for any damage, data loss, or issues that may arise from using this repository.

## Cluster Setup

### ubuntu Nodes

Control Node
```
#Install w/o Traefik
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="--disable traefik" K3S_KUBECONFIG_MODE="644" sh -

#Get Token
cat /var/lib/rancher/k3s/server/node-token

```

Worker Nodes
```
#Install
curl -sfL https://get.k3s.io | K3S_URL=https://<ip>:6443 K3S_TOKEN=<token> sh -
```

### Setup Flux
Note: This seems to work better if you remove the deployments (aka the apps) first, let it come up and stablize, reboot may be neccessary. Setup what you want in longhorn, then add in the deployments.

Discord: You will need to create a secret called discord-url in the flux-system namespace.

```
flux bootstrap github --components-extra=image-reflector-controller,image-automation-controller --owner=dyslexicjedi --repository=homelab --branch=main --path=clusters/homelab --personal --token-auth
```