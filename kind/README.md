# Project Title

## Table of Contents

- [About](#about)
- [Getting Started](#getting_started)
- [Usage](#usage)
- [Contributing](../CONTRIBUTING.md)

## About <a name = "about"></a>

choco install kind

https://kind.sigs.k8s.io/



kind get clusters

kind create cluster --name kind-cluster-lou --config kind-config.yaml

kubectl cluster-info --context kind-kind-cluster-lou
```
λ kubectl cluster-info --context kind-kind-cluster-lou
Kubernetes control plane is running at https://127.0.0.1:51014
CoreDNS is running at https://127.0.0.1:51014/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

cat ~/.kube/config
ou voce pode abrir direto em 
notepad.exe $env:USERPROFILE\.kube\config


https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/
kubectl config view



docker run -d --name rancher  --restart=unless-stopped  -p 80:80 -p 443:443 --privileged rancher/rancher:latest