# Monitoring Setup with Prometheus-Operator
Let's get started with the setup.

## Deployment

In my opinion, I would deploy Prometheus and the other components using the prometheus-operator. 
Since this already brings everything important with itself.

### Prometheus Operator
The Prometheus Operator provides Kubernetes native deployment and management of Prometheus and related monitoring components. The purpose of this project is to simplify and automate the configuration of a Prometheus based monitoring stack for Kubernetes clusters.

The Prometheus operator includes, but is not limited to, the following features:
- Kubernetes Custom Resources: Use Kubernetes custom resources to deploy and manage Prometheus, Alertmanager, and related components.
- Simplified Deployment Configuration: Configure the fundamentals of Prometheus like versions, persistence, retention policies, and replicas from a native Kubernetes resource.
- Prometheus Target Configuration: Automatically generate monitoring target configurations based on familiar Kubernetes label queries; no need to learn a Prometheus specific configuration language.


### Installation
#### Get the kube-prometheus project
For a quick start we are going to deploy a compiled version of the Kubernetes manifests.
```bash
git clone https://github.com/prometheus-operator/kube-prometheus.git
cd kube-prometheus/
```

Create the namespace and CRDs, and then wait for them to be availble before creating the remaining resources
```bash
kubectl create -f manifests/setup
until kubectl get servicemonitors --all-namespaces ; do date; sleep 1; echo ""; done
kubectl create -f manifests/
```

We create the namespace and CustomResourceDefinitions first to avoid race conditions when deploying the monitoring components. Alternatively, the resources in both folders can be applied with a single command kubectl create -f manifests/setup -f manifests, but it may be necessary to run the command multiple times for all components to be created successfullly.

