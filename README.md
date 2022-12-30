# elastic-8


1.  LucaWintergerst /observability-example

```https://github.com/LucaWintergerst/observability-example```

```
ElasticCC: Getting Started With Elastic APM
   
   https://www.youtube.com/watch?v=jRSGj65YLA8
```



2. Henrique mauri

```https://www.youtube.com/watch?v=Rb-3tZq759Q```

```https://github.com/hgmauri```

```https://henriquemauri.net/```


## DOCUMENTAÇÕES

> https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-date-format.html

> https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-params.html


## GROK DEBUG

* https://grokdebug.herokuapp.com/

* https://grokdebugger.com/

* https://regex101.com/

## LOGSTASH PATTERNS

* https://github.com/hpcugent/logstash-patterns/blob/master/files/grok-patterns

* https://discuss.elastic.co/t/what-is-greedydata/122078

## DOCUMENTACOES

* https://frednotes.wordpress.com/2021/08/25/wildfly-elastic/

> Using Grok with Elasticsearch to add structure to your data

* https://alexmarquardt.com/using-grok-with-elasticsearch-to-add-structure-to-your-data/

> Common Logstash Use cases with GROK, JSON and Mutate filters.
* https://itnext.io/common-logstash-use-cases-with-grok-json-and-mutate-filters-elk-logstash-in-docker-filebeat-871ed58c7651


## GROK PATTERNES

``` Grok Pattern

2722-12-29 03:02:19,305 ERROR [stderr] (default task-2396) Caused by: br.com.microsoft.jape.PersistenceException: Projeto já concluído. Não pode ser.

(?:%{TIMESTAMP_ISO8601:data}) (?:%{LOGLEVEL:level}) \[(%{WORD:method})\] \(%{WORD:method2)\) (?<message>.*)$

```
 a  asdada

```
(?:%{TIMESTAMP_ISO8601:data}) (?:%{LOGLEVEL:level}) \[(%{WORD:method})\] \(%{WORD:method2)\) (?<message>.*)$
```
