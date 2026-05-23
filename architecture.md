# Kubernetes (K8s) Notes

# What is Kubernetes?

Kubernetes is a container orchestration platform used to:
- automate deployment
- scaling
- healing
- management of containers

Kubernetes mainly manages Docker/containerized applications.

---

# History

Google internally created a tool called:
```text
Borg
```

for:
- auto scaling
- auto healing
- large-scale container management

Later Google donated Kubernetes to:
```text
CNCF (Cloud Native Computing Foundation)
```

which comes under:
```text
Linux Foundation
```

Kubernetes short form:
```text
K8s
```

Reason:
- "K" + 8 letters + "s"

---

# What is Cluster?

Kubernetes works on:
```text
Cluster
```

Cluster means:
```text
multiple machines/nodes connected together
```

to run applications.

---

# Types of Nodes

## 1. Master Node / Control Plane

Controls the entire Kubernetes cluster.

Responsibilities:
- scheduling
- monitoring
- healing
- orchestration
- maintaining desired state

Usually one or more master nodes exist.

Master node does NOT generally run application workload.

---

## 2. Worker Node

Actual applications run here.

Worker nodes contain:
- pods
- containers
- application workloads

There can be multiple worker nodes.

---

# Communication Between Nodes

Communication happens using:
```text
CNI (Container Network Interface)
```

CNI handles:
- pod networking
- IP assignment
- inter-node communication

Examples:
- Calico
- Flannel
- Cilium

---

# Kubernetes Architecture

```text
                 Kubernetes Cluster
-------------------------------------------------

                Control Plane
             (Master Node Components)

        API Server
        Scheduler
        Controller Manager
        etcd
        Cloud Controller Manager

-------------------------------------------------

                 Worker Nodes

        kubelet
        kube-proxy
        Container Runtime
        Pods

-------------------------------------------------
```

---

# Control Plane Components

# API Server

API Server is the:
```text
front door of Kubernetes
```

All requests first go to API Server.

Examples:
- kubectl commands
- UI requests
- automation tools

API Server:
- validates request
- processes request
- communicates with cluster components

---

# etcd

etcd is:
```text
Kubernetes database
```

Stores:
- cluster state
- pod information
- node information
- configurations
- secrets

VERY important component.

If etcd lost:
```text
cluster state lost
```

---

# Scheduler

Scheduler decides:
```text
which worker node should run pod
```

It checks:
- CPU
- memory
- resource availability
- constraints
- taints/tolerations

Example:
```text
Backend pod should run on Worker Node 2
```

---

# Controller Manager

Controller Manager continuously monitors cluster state.

If actual state != desired state:
```text
controller fixes it
```

Example:
- Pod crashed
- Kubernetes automatically recreates pod

This provides:
```text
self-healing
```

---

# Cloud Controller Manager

Used in cloud platforms like:
- AWS
- Azure
- GCP

Helps Kubernetes interact with cloud services:
- load balancer
- storage
- VM instances

Examples:
- EKS
- AKS
- GKE

---

# Worker Node Components

# kubelet

kubelet is:
```text
agent running on worker node
```

Responsibilities:
- talks with API Server
- ensures pods running properly
- monitors containers

If pod crashes:
```text
kubelet reports status
```

---

# kube-proxy

kube-proxy handles:
```text
network communication
```

Responsibilities:
- pod-to-pod communication
- service networking
- traffic routing

Acts like:
```text
network traffic manager
```

---

# Container Runtime

Software responsible for running containers.

Examples:
- containerd
- CRI-O
- Docker (older setups)

Container runtime actually:
- pulls images
- starts containers
- stops containers

---

# Other Important Kubernetes Components

# Pod

Smallest deployable unit in Kubernetes.

Pod can contain:
- one container
- multiple containers

Usually:
```text
1 Pod = 1 application container
```

Example:
```text
nginx pod
python pod
mysql pod
```

---

# Service

Pods are temporary.

Their IP changes frequently.

Service provides:
```text
stable network endpoint
```

for accessing pods.

Types:
- ClusterIP
- NodePort
- LoadBalancer

---

# Volume

Used for:
```text
persistent storage
```

without losing data.

Example:
```text
MySQL database storage
```

---

# Namespace

Namespace divides cluster resources logically.

Used for:
- teams
- projects
- environments

Example:
```text
dev namespace
test namespace
prod namespace
```

---

# Ingress

Ingress manages:
```text
external HTTP/HTTPS access
```

Acts like:
```text
application entry point
```

Routes traffic to services.

Example:
```text
app.company.com → frontend service
api.company.com → backend service
```

---

# Ways to Create Kubernetes Cluster

# kubeadm

Used to create:
```text
bare metal Kubernetes cluster
```

Mostly used:
- learning
- on-premises setup

---

# Kind (Kubernetes in Docker)

Runs Kubernetes nodes as:
```text
Docker containers
```

Good for:
- local practice
- testing

---

# Minikube

Single-node local Kubernetes cluster.

Best for:
```text
beginners
```

Very commonly used for learning.

---

# Managed Kubernetes Services

## EKS
Amazon Elastic Kubernetes Service

## AKS
Azure Kubernetes Service

## GKE
Google Kubernetes Engine

Cloud provider manages:
- control plane
- upgrades
- scaling

---

# Killercoda

Online Kubernetes practice lab.

Useful for:
- hands-on learning
- no local installation

---

# K8s Playground

Browser-based Kubernetes learning environment.

---

# Important Beginner Understanding

Docker:
```text
runs containers
```

Kubernetes:
```text
manages containers at scale
```

---

# Real-World Flow

Developer:
```text
build Docker image
        ↓
push image to registry
        ↓
Kubernetes pulls image
        ↓
Pods created
        ↓
Service exposes application
```


---

# Important Keywords

| Term | Meaning |
|---|---|
| Cluster | Group of nodes |
| Node | Machine/server |
| Pod | Smallest deployable unit |
| Service | Stable networking endpoint |
| Ingress | External traffic routing |
| etcd | Kubernetes database |
| Scheduler | Decides pod placement |
| kubelet | Worker node agent |
| kube-proxy | Network traffic manager |
| Namespace | Logical isolation |
