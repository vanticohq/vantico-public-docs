# Exposição Excessiva de Dados

Em um programa privado de bug bounty, a resposta à solicitação de login tinha três parâmetros: `isAdmin`, `isStaff` e `isSupport`. Todos os três foram inicialmente definidos como `false`. Configurando eles para `true` concedeu acesso a um novo endpoint que permitiu pesquisar empresas usando seus IDs de registro.

Uma solicitação GET para o seguinte endpoint foi feita ao procurar uma empresa:



```
GET /company/companies.json?registration number=123456&page=1&per=1 HTTP/1.1
Host: api.site.com

```



A `GUI`exibia apenas o `nome da empresa`. No entanto, ao usar o Burp Suite para analisar a resposta, `informações pessoais confidenciais` da empresa foram expostas. O divulgado as informações incluíam `nome da empresa`, `e-mail`, `número de telefone` e `endereço completo (Rua, Cidade, País).`

Esses dados eram inicialmente exclusivos de uma única empresa e qualquer tentativa de força bruta não permitido nesse endpoint devido à presença de proteção de limite de taxa.

Limpei os valores de todos os parâmetros e enviei a solicitação com os campos vazios.



```
GET /company/companies.json?registration number=&page=&per= HTTP/1.1
Host: api.site.com
```



Como resultado, as informações confidenciais de todas as empresas do programa foram expostas. Era um Divulgação em massa de PII afetando mais de 40 mil empresas.



Quando você se depara com um `IDOR` que requer `UUID`, como:



```
DELETE /vl/api tokens/d90093bc-b2f7-11ed-afal-0242ac120002 HTTP/2
Host: api.site.com
Cookie:
```



Se você não conseguir encontrar o `UUID` em nenhum lugar, tente encontrar endpoints que divulguem o  `UUID` dentro da mesma organização.



```
GET /v1/api tokens/ HTTP/2
Host: api.site.com
Cookie:
```



Agora verifique se você pode acessar o mesmo endpoint usando uma conta de usuário com `privilégios mais baixos.` Se puder, você poderá explorar o `IDOR` usando uma conta de usuário com `privilégios mais baixos.`
