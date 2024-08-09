# BucketLoot

É uma ferramenta criada para automatização do processo de encontrar **secrets** dentro de um **bucket S3.**



**Como utilizar?**

```
./bucketloot (link s3)
```

* Funcionamento básico



```
./bucketloot (link s3) -dig
```

* Extrair e escanear todos os alvos que não estão nos storage buckets



```
./bucketloot (link s3) -full
```

* Fazer um scan além dos 1000 arquivos



```
./bucketloot (link s3) -log-erros
```

* Log de erros no final da output



```
./bucketloot (link s3) -max-size string
```

* Tamanho máximo do arquivo (em bytes)



```
./bucketloot (link s3) -notify
```

* Notificar usando webhooks quando a ferramenta encontrar algum exposição de segurança



```
./bucketloot (link s3) -save string
```

* Salvar o output, podendo ser tanto como .txt quanto .json



```
./bucketloot (link s3) -search string
```

* Palavras para buscar durante o scan



```
./bucketloot (link s3) -slow
```

* Setar modo de scan para lento



Para baixar a ferramenta:

{% embed url="https://github.com/redhuntlabs/BucketLoot" %}

