# Project Title

## Table of Contents

- [About](#about)
- [Getting Started](#getting_started)
- [Usage](#usage)
- [Contributing](../CONTRIBUTING.md)

## About <a name = "about"></a>

Write about 1-2 paragraphs describing the purpose of your project.

## Getting Started <a name = "getting_started"></a>


helm upgrade --install ingress-nginx ingress-nginx \
  --repo https://kubernetes.github.io/ingress-nginx \
  --namespace ingress-nginx --create-namespace

kubectl get pods --namespace=ingress-nginx

kubectl wait --namespace ingress-nginx \
  --for=condition=ready pod \
  --selector=app.kubernetes.io/component=controller \
  --timeout=120s


kubectl create deployment demo --image=httpd --port=80
kubectl expose deployment demo

kubectl create ingress demo-localhost --class=nginx \
  --rule="demo.localdev.me/*=localhost:8090"

kubectl port-forward --namespace=ingress-nginx service/ingress-nginx-controller 8090:80

# -----------

helm upgrade --install ingress-nginx ingress-nginx --repo https://kubernetes.github.io/ingress-nginx --namespace ingress-nginx --create-namespace

kubectl create deployment simoes --image=httpd --port=80 --namespace ingress-nginx

kubectl expose deployment simoes

kubectl create ingress simoes-localhost --class=nginx --rule="demo.localdev.me/*=simoes:80"

kubectl port-forward --namespace=ingress-nginx service/ingress-nginx-controller 8030:80


kubectl delete ingress simoes
kubectl delete deployment simoes

