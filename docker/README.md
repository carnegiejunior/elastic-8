# Project Title

## Table of Contents

- [About](#about)
- [Getting Started](#getting_started)
- [Usage](#usage)
- [Contributing](../CONTRIBUTING.md)

## About <a name = "about"></a>




docker run --name es01 --net elastic -p 9200:9200 -p 9300:9300 -it docker.elastic.co/elasticsearch/elasticsearch:8.2.3
docker cp es01:/usr/share/elasticsearch/config/certs/http_ca.crt .
curl --cacert http_ca.crt -u elastic https://localhost:9200


## Rancher <a name = "rancher"></a>

```
docker run -d --name rancher --net elastic  --restart=unless-stopped  -p 8010:80 -p 44310:443 --privileged rancher/rancher:latest
```

```
docker run -d --name rancher --restart=unless-stopped  -p 80:80 -p 443:443 --privileged rancher/rancher:latest
```

λ docker logs  e87fcc8f4e1a  2>&1 | grep "Bootstrap Password:"
    2022/08/29 17:53:36 [INFO] Bootstrap Password: 245tm4vxh4hjpnxvb24x8ckrk7zxw96lhfr247xh8fxnfxmftwzqm

https://localhost:44310/
    
    password: 2tBvSh1y47LvwhLW


## Rancher <a name = "rancher"></a>

kubectl port-forward nginx-simoes-02-6595874d85-98f49 8000:80

## kubectl <a name = "kubectl"></a>

kubectl create deploy nginx --image=nginx:1.6-alpine

kubectl get po

kubectl get rs

kubectl delete deploy/nginx

kubectl create deploy nginx --image=nginx:1.16-alpine --dry-run=client -o yaml

kubectl scale deploy/nginx --replicas=3

kubectl run nginx --image=nginx

kubectl get pods -o wide

Kubernetes Concepts - https://kubernetes.io/docs/concepts/
Pod Overview- https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/

kubectl create -f pod-container.yml
kubctl apply -f pod-container.yml


kubectl create clusterrolebinding cluster-admin-binding --clusterrole cluster-admin --user kind-kind-cluster-lou





fontes
* https://fabiosilva.com.br/2021/03/02/rancherkubernetes/
* 