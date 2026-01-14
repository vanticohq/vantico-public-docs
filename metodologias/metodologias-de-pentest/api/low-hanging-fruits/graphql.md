# GraphQL

#### Ausência de controle anti automação

Verificar se a API GraphQL possui limite de requisições por minuto. Deve ser testado fazendo 20+ requests da mesma query em um curto período de tempo.

***

#### Erros descritivos

Verificar se erros de query inválida expõem stack traces, nomes de tabelas SQL, resolvers internos ou dados sensíveis. Deve ser testado com query malformada como { user(id: "invalid") { secretField } }.\
Erros devem ser sanitizados via formatError para mostrar apenas códigos/mensagens genéricas.

***

#### Enumeração de IDs

Verificar se IDs sequenciais (1,2,3...) podem ser enumerados via queries GraphQL sem autenticação. Deve ser testado com { user(id: "1") { name }, user(id: "2") { name } }.\
Usar UUIDs v4 ou exigir autenticação em todas as queries de recursos sensíveis.

***

#### Instropecção habilitada

Verificar se a query \_\_schema { types { name } } retorna o schema completo da API. Deve ser testado colando diretamente no endpoint GraphQL.
