# Como funcionam os fusos horários no Kibana?

Como configurar o fuso horário do Elasticsearch UTC padrão para carimbos de data/hora
     
O Kibana usa o fuso horário do seu navegador por padrão, mas é possível alterar isso se você precisar.
         
## Como faço para alterar o fuso horário?

Para alterar o fuso horário navegue até o seguinte:

```
Kibana > Gerenciamento > Configurações avançadas
```

Você verá muitas configurações aqui que controlam o comportamento do Kibana, uma das quais é o fuso horário. A configuração que você está procurando é a seguinte:

formato de data: tz

Você pode ver que 'Navegador' é o fuso horário selecionado no momento. Clique no botão 'Editar' para este item e você verá uma lista suspensa.

Escolha o fuso horário que você precisa na lista e pressione o botão Salvar. Se você agora clicar em 'Descobrir' no menu à esquerda para retornar aos resultados, verá que os dados agora são exibidos usando o novo fuso horário que você selecionou.

Dica: Tanto o Elasticsearch quanto o Logstash usam o fuso horário UTC para carimbos de data/hora. Embora isso possa ser alterado, é recomendável manter o padrão e deixar os ajustes no Kibana ou em qualquer outra camada de apresentação que você possa usar.
