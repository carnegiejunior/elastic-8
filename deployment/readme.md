kubectl apply -f <nome-arquivo>.yaml

kubectl port-foward <service>/pod <porta>

### nginx07.yaml
https://kubernetes.io/docs/tasks/run-application/run-stateless-application-deployment/




----------
## Criar pod e expor a porta para poder acessar.

fonte:
```
https://kubernetes.io/docs/tasks/access-application-cluster/port-forward-access-application-cluster/
```

kubectl apply -f https://k8s.io/examples/application/deployment.yaml

kubectl get pods -o wide

kubectl get all

kubectl expose deployment nginx-deployment --type=LoadBalancer --port=80

kubectl port-forward deployment.apps/nginx-deployment 8081:80