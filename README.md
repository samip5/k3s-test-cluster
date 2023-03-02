## k3s-test-cluster

This is a TEST/DEV CLUSTER running on two Raspberry Pi 4s as that was the only amount of hardware I had free for it.

### :open_file_folder:&nbsp; Repository structure

The Git repository contains the following directories under `cluster` and are ordered below by how Flux will apply them.

- **flux** directory is the entrypoint to Flux
- **bootstrap** directory contains a simple Kustomize resource to deploy Flux to an empty cluster
- **apps** directory is where my common applications (grouped by namespace) are placed.

```
kubernetes
├── apps
├── bootstrap
└── flux
```

### :wrench:&nbsp; Tools

| Tool                                                               | Purpose                                                             |
|--------------------------------------------------------------------|---------------------------------------------------------------------|
| [ansible](https://www.ansible.com)                                 | Preparing Ubuntu for Kubernetes and installing k3s                  |
| [flux](https://toolkit.fluxcd.io/)                                 | Operator that manages your k8s cluster based on your Git repository |
| [sops](https://github.com/mozilla/sops)                            | Encrypts k8s secrets with GnuPG                                     |


## 💻 Nodes
| Node                     | Hostname | RAM  | Storage       | Function          | Operating System
| ------------------------ |--|------| ------------- | ----------------- |------------------|
| Raspberry Pi 4 Model B   | m1 | 8GB  | 64GB SSD     | Kube Master  | Ubuntu 22.04 LTS |
| Raspberry Pi 4 Model B   | w1 | 4GB  | 1TB HDD   | Kube Worker   | Ubuntu 22.04 LTS |

## Network

All nodes are connected to a dual-stack network, with private IPv4 and public IPv6.  
Kubernetes nodes are on their own VLAN.
