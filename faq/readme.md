

1. faq/img/ssl.ca_trusted_fingerprint.PNG
<p align="left">
  <a href="" rel="noopener">
 <img  height=600px src="https://github.com/lourranio/elastic-8/blob/118e9a73bb9fb1d9416af849952cc7f7e01ef84a/faq/img/ssl.ca_trusted_fingerprint.PNG" alt="ssl.ca_trusted_fingerprint"></a>
</p>

2. 
PS C:\Heartbeat> .\heartbeat.exe setup
Overwriting ILM policy is disabled. Set `setup.ilm.overwrite: true` for enabling.

edit this file "heartbeat.yml", and add isso > ```setup.ilm.overwrite: true```

```
heartbeat.monitors:
- type: http
  # Set enabled to true (or delete the following line) to enable this example monitor
 ...
setup.ilm.overwrite: true
```

<p align="left">
  <a href="" rel="noopener">
 <img  height=600px src="https://github.com/lourranio/elastic-8/blob/09d1ef90e2905c36193d6194c912137c742b266c/faq/img/problema-heartbeat.PNG" alt="ssl.ca_trusted_fingerprint"></a>
</p>


## 3

```
PS C:\Heartbeat> .\install-service-heartbeat.ps1
.\install-service-heartbeat.ps1 : O arquivo C:\Heartbeat\install-service-heartbeat.ps1 não pode ser carregado porque a
execução de scripts foi desabilitada neste sistema. Para obter mais informações, consulte about_Execution_Policies em
https://go.microsoft.com/fwlink/?LinkID=135170.
No linha:1 caractere:1
+ .\install-service-heartbeat.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ErrodeSegurança: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
 
```


### Solucao
https://docs.microsoft.com/pt-br/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2

```
PS C:\Heartbeat> powershell.exe -ExecutionPolicy Unrestricted
Windows PowerShell
Copyright (C) Microsoft Corporation. Todos os direitos reservados.

Experimente a nova plataforma cruzada PowerShell https://aka.ms/pscore6

PS C:\Heartbeat> .\install-service-heartbeat.ps1

Status   Name               DisplayName
------   ----               -----------
Stopped  heartbeat          heartbeat


PS C:\Heartbeat>
```

<p align="left">
  <a href="" rel="noopener">
 <img  height=200px src="https://github.com/lourranio/elastic-8/blob/19c0bc3de8e994bd63533b6fce7900ead6cc8932/faq/img/solucao.PNG" alt="ssl.ca_trusted_fingerprint"></a>
</p>


## 4

* ```server.publicBaseUrl: "https://<dominio>.com.br:5601"```

* ```server.name: "your-hostname"```

* ```elasticsearch.hosts: ["http://localhost:9200"]```
ou
```elasticsearch.hosts: ["https://localhost:9200"]```

* ```#elasticsearch.ssl.verificationMode: none```
(irá ignorar os avisos do certificado q foi auto gerado)


## 5 discovery.type: single-node
https://www.elastic.co/guide/en/elasticsearch/reference/current/bootstrap-checks.html#single-node-discovery

in elasticsearch.yml
```
network.host: 0.0.0.0
discovery.type: single-node
```
and make sure you have cluster.initial_master_nodes off

```# cluster.initial_master_nodes: ["node-1", "node-2"]```

## 6 

<p align="left">
  <a href="" rel="noopener">
 <img  height=600px src="https://github.com/lourranio/elastic-8/blob/6992d06dd0c5be4ed0ee5af4304cef7243ba5352/faq/img/http_ca.PNG" alt="http_ca.crt"></a>
</p>

https://codebeautify.org/yaml-validator


## 7
Certbot

```https://discuss.elastic.co/t/issues-with-certbot-certificates-and-kibana/282270```

```
xpack.security.enabled: true
xpack.security.transport.ssl.enabled: true
xpack.security.transport.ssl.verification_mode: certificate
xpack.security.transport.ssl.key: /etc/elasticsearch/certs/privkey1.pem
xpack.security.transport.ssl.certificate: /etc/elasticsearch/certs/cert1.pem
xpack.security.transport.ssl.certificate_authorities: [ "/etc/elasticsearch/certs/fullchain1.pem" ]
xpack.security.http.ssl.enabled: true
xpack.security.http.ssl.verification_mode: certificate
xpack.security.http.ssl.key: /etc/elasticsearch/certs/privkey1.pem
xpack.security.http.ssl.certificate: /etc/elasticsearch/certs/cert1.pem
```

## 8 
"  Unable to retrieve version information from Elasticsearch nodes. "

* 1 Solucao : Usuario kibana errado. Correto. kibana_system
  
  Rest password for kibana_system user
	```/usr/share/elasticsearch/bin/elasticsearch-reset-password -u kibana_system```
  
* 2 Solucao : elasticsearch.hosts: ["https://localhost:9200"] . Add um S  em httpS.


## 9
CRIACAO DA API KEY - heartbeat

Solucao: http://192.168.0.80:5601/app/management/security/api_keys/

```
root@elk:/home/# heartbeat setup
Exiting: couldn't connect to any of the configured Elasticsearch hosts. Errors: [error connecting to Elasticsearch at https://localhost:9200: 401 Unauthorized: {"error":{"root_cause":[{"type":"security_exception","reason":"unable to authenticate user [elastic] for REST request [/]","header":{"WWW-Authenticate":["Basic realm=\"security\" charset=\"UTF-8\"","Bearer realm=\"security\"","ApiKey"]}}],"type":"security_exception","reason":"unable to authenticate user [elastic] for REST request [/]","header":{"WWW-Authenticate":["Basic realm=\"security\" charset=\"UTF-8\"","Bearer realm=\"security\"","ApiKey"]}},"status":401}]
```

## 10

```
root@elk-aquario:/home/vagrant# heartbeat setup
Overwriting ILM policy is disabled. Set `setup.ilm.overwrite: true` for enabling.

Index setup finished.
```

Solucao: editar o arquivo : 
```vim /etc/heartbeat/heartbeat.yml``` 

e adicionar o parametro na ultima linha 
```setup.ilm.overwrite: true```

## 11 

``` ERROR: [1] bootstrap checks failed. You must address the points described in the following [1] lines before starting Elasticsearch. ```

Docker Desktop ou rancher desktop com WSL on Windows

Faca a mudanca no ```vm.max_map_count``` via wsl

```
wsl

sudo sysctl -w vm.max_map_count=262144
```
