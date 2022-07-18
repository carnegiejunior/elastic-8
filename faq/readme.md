

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
