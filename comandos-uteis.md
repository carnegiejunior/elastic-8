# COMANDOS UTEIS NO ELASTIC


## VER OS DADOS DO DISCO
curl -XGET 'elasticsearch.internal:9200/_cat/allocation?v&pretty'
```
shards disk.indices disk.used disk.avail disk.total disk.percent host         ip           node
   161       72.8gb   107.5gb    283.8gb    391.4gb           27 192.168.0.42 192.168.0.42 srv
   133                                                                                     UNASSIGNED
```
