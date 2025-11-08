# Infrastructure as Code

This repository contains an Infrastructure as Code (IaC) implementation for a modern Kubernetes platform using Talos OS and Flux. This is for my own homelab, and not an example or how-to.

## Overview

This implementation leverages:

- **[Talos OS](https://www.talos.dev/)**: A modern, secure, and immutable Linux distribution designed specifically for Kubernetes
- **[Kubernetes](https://kubernetes.io/)**: Container orchestration platform for automating deployment, scaling, and management of containerized applications
- **[Flux](https://fluxcd.io/)**: GitOps toolkit for keeping Kubernetes clusters in sync with configuration sources


## Architecture

The infrastructure is managed using GitOps principles, where:

1. **Talos OS** provides the minimal, secure operating system layer optimized for running Kubernetes
2. **Kubernetes** serves as the orchestration platform for containerized workloads
3. **Flux** continuously reconciles the desired state (defined in Git) with the actual cluster state

## Disclaimer

**USE AT YOUR OWN RISK**

This repository is a personal homelab project and is provided "as is" without warranty of any kind, express or implied. The configurations and code contained herein are specific to my environment and may not be suitable for your use case.

- ⚠️ No warranty or guarantee of functionality
- ⚠️ Not intended as production-ready code
- ⚠️ Use at your own risk and discretion
- ⚠️ Always review and test configurations before applying to your infrastructure


The author(s) assume no responsibility for any damage, data loss, or issues that may arise from using this repository.