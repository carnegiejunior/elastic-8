# Como criar um arquivo YAML para subir um Pod com nginx
-- fonte : https://ed.blog.br/kubectl-como-criar-um-arquivo-yaml-para-subir-um-pod-com-nginx/

Comando:
```
kubectl run nginx-yaml --image=nginx --restart=Never --dry-run=client -n elastic -o yaml > pod.yaml
```
Teste:

cat pod.yaml

Resultado:

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: nginx-yaml
  name: nginx-yaml
  namespace: elastic
spec:
  containers:
  - image: nginx
    name: nginx-yaml
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Never
status: {}



# ----------------------

https://kubernetes.io/docs/tasks/run-application/run-stateless-application-deployment/
