# GraphQL

É uma linguagem de consulta e uma estrutura de execução para APIs que permite que os clientes solicitem apenas os dados específicos de que precisam, em vez de receberem uma resposta completa com todos os dados disponíveis. Foi desenvolvido pelo Facebook em 2012 e lançado publicamente em 2015.A principal diferença entre GraphQL e as abordagens tradicionais de API, como REST (Representational State Transfer), é que o GraphQL coloca o controle nas mãos dos clientes. Em vez de o servidor determinar quais dados são retornados em uma resposta, o cliente especifica exatamente quais campos e relacionamentos ele deseja que a API retorne. Isso torna as consultas mais eficientes e flexíveis, pois os clientes podem buscar apenas o que precisam, evitando a sobrecarga de dados.Principais características do GraphQL:

* Consulta única: Em uma única consulta GraphQL, você pode solicitar dados de várias entidades e seus relacionamentos, em vez de fazer várias chamadas de API para obter dados separados.
* Tipo de sistema: O GraphQL define um sistema de tipos para os dados que podem ser consultados. Isso ajuda a documentar a API de forma clara e permite a validação de consulta em tempo de execução.
* Introspecção: O GraphQL permite que você consulte o esquema da API para descobrir quais tipos de dados estão disponíveis, quais consultas podem ser feitas e quais campos estão disponíveis em cada tipo.
* Mutação: Além de consultas, o GraphQL suporta mutações, que permitem que os clientes modifiquem dados no servidor, como criar, atualizar ou excluir registros.
* Subscrições: O GraphQL também suporta subscrições em tempo real, permitindo que os clientes recebam atualizações quando os dados mudam no servidor.

No geral, o GraphQL é uma tecnologia poderosa para o desenvolvimento de APIs flexíveis e eficientes, especialmente em situações onde os requisitos de consulta dos clientes podem variar amplamente ou quando se deseja reduzir a sobrecarga de dados nas respostas da API.

#### Dica

Como apresentado na Introdução, o GraphQL possuí uma funcionalidade de Instropecção: permite que você consulte o esquema da API para descobrir quais tipos de dados estão disponíveis, quais consultas podem ser feitas e quais campos estão disponíveis em cada tipo.\
No entanto, essa funcionalidade pode ser desabilitada. Caso isso aconteça existe uma alternativa que é usar ferramentas como a clairvoyance ([https://github.com/nikitastupin/clairvoyance](https://github.com/nikitastupin/clairvoyance)), basicamente ela usa uma wordlist para tentar fazer queries e observa as mensagens de retorno, que possuí os nomes dos campos corretos e a partir disso vai montando uma base de campos conhecimentos e também tentando inferir novos.

#### Ferramentas de apoio

Um equivalência ao Postman/Insominia de API REST é o Altair ([https://altairgraphql.dev](https://altairgraphql.dev/)), ele fica a frente dessas ferramentas e até mesmo de algumas extensões do Burp Suite pois tem funções de auto complete e geração de documentação automática.Se você precisa de um apoio visual para entender melhor as relações de objetos e atributos em uma API GraphQL, o Voayger é uma ótima ferramenta para isso: [https://apis.guru/graphql-voyager/](https://apis.guru/graphql-voyager/)
