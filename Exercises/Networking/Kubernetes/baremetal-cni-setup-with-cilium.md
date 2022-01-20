# Baremetal CNI Setup with Cilium
In a freshly set up Kubernetes cluster, we need a so-called CNI. This CNI is not always present after installation.

## What is a Container Network Interface (CNI)?
CNI is a network framework that allows the dynamic configuration of networking resources through a group of Go-written specifications and libraries. The specification mentioned for the plugin outlines an interface that would configure the network, provisioning the IP addresses, and mantain multi-host connectivity.

In the Kubernetes context, the CNI seamlessly integrates with the kubelet to allow automatic network configuration between pods using an underlay or overlay network. An underlay network is defined at the physical level of the networking layer composed of routers and switches. In contrast, the overlay network uses a virtual interface like VxLAN to encapsulate the network traffic.

Once the network configuration type is specified, the runtime defines a network for containers to join and calls the CNI plugin to add the interface into the container namespace and allocate the linked subnetwork and routes by making calls to IPAM (IP Address Management) plugin.

In addition to Kubernetes networking, CNI also supports Kubernetes-based platforms like OpenShift to provide a unified container communication across the cluster through software-defined networking (SDN) approach.

### What is Cilium?
Cilium is an open source project to provide networking, security, and observability for cloud native environments such as Kubernetes clusters and other container orchestration platforms.

At the foundation of Cilium is a new Linux kernel technology called eBPF, which enables the dynamic insertion of powerful security, visibility, and networking control logic into the Linux kernel. eBPF is used to provide high-performance networking, multi-cluster and multi-cloud capabilities, advanced load balancing, transparent encryption, extensive network security capabilities, transparent observability, and much more.
