# Enumeração de Subdomínios

Para realizar uma enumeração de subdomínios, temos duas maneiras de se fazer, de forma manual ou automatizada. A forma mais eficiente de se realizar seria combinando as duas.



**Forma automatizada:**&#x20;

A ferramenta _Amass_ foi criada pela OWASP e ela tem como função realizar uma descoberta de ativos externos usando a coleta de informações, que podem ser desde APIs, certificados, DNS, rotas, web scraping, arquivos da web (_Wayback_) e WHOIS.&#x20;

Ao executar a ferramenta você pode escolher por dois tipos de busca, seja **intel** ou **enum**.



**Intel:**&#x20;

Irá descobrir namespaces e subdomínios para enumeração.



**Enum:**&#x20;

Irá realizar a enumeração completa, utilizando mais ferramentas que o Intel, dentro deste módulo você pode usar de forma **-passive** ou **-active**, a diferença é que o **passive** vai ser um scan mais rápido, com menos informações e de maneira não tão precisa. Enquanto o **active** vai trazer bem mais informações e de maneira muito mais precisa.



Para utilizar a ferramenta é bem simples, primeiro de tudo você deve configurar as chaves APIs que irá utilizar, para isso deve ir até:

A pasta onde instalou o Amass > _examples_ > edite o arquivo "_datasources.yaml_" inserindo suas chaves API dentro.



Desta maneira a ferramenta poderá puxar as infos de APIs, em sequência agora podemos realizar um scan básico como:



```
amass enum -d (dominio.com)
```

E através deste ir aperfeiçoando, como:

```
amass enum -active -d (dominio.com)
```

Lista de domínios:

```
amass enum -active -df (dominios.txt)
```



**Forma manual:**&#x20;

Uma das maneiras mais interessantes de enumerarmos subdomínios de forma manual é através de arquivos js presentes no código da aplicação (CTRL+U), como o **main.js** ou o **app.js**, quando visualizado os arquivos, dentro deles pode conter informações sobre subdomínios ou até mesmo alguns secrets da aplicação.



**OpenINTEL:**

{% embed url="https://openintel.nl/team/" %}

