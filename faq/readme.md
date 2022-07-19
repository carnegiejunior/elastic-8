

1. faq/img/ssl.ca_trusted_fingerprint.PNG
<p align="left">
  <a href="" rel="noopener">
 <img  height=200px src="https://github.com/lourranio/elastic-8/blob/118e9a73bb9fb1d9416af849952cc7f7e01ef84a/faq/img/ssl.ca_trusted_fingerprint.PNG" alt="ssl.ca_trusted_fingerprint"></a>
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
 <img  height=200px src="https://github.com/lourranio/elastic-8/blob/09d1ef90e2905c36193d6194c912137c742b266c/faq/img/problema-heartbeat.PNG" alt="ssl.ca_trusted_fingerprint"></a>
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

```server.publicBaseUrl: "https://<dominio>.com.br:5601"```
