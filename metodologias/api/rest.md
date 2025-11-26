# REST

Normalmente o público-alvo de uma API são desenvolvedores, em um primeiro momento, utilize a mesma como se fosse um; entenda a visão que o usuário final tem e só depois parta para raciocínios sobre vulnerabilidades na mesma;

***

**IDOR - Insecure Direct Object Reference**\
Encontrando ideias de ataque de vetores:1. O que eles usam para autorização? (JWT, chaves de API, cookies, tokens) Dica: descubra isso substituindo a autorização de alto privilégio por autorização de privilégio inferior e vendo com o que o servidor responde;2. Entenda como eles usam IDs, hashes e suas APIs. Faça isso consultando a documentação da API, se houver;\
Dicas de reconhecimento:1. Tente pesquisar UUIDs em mecanismo de pesquisa, ex: google dork para parâmetros de URL;2. Use ferramentas como WaybackURLS ou gau e grep para UUIDs, ids e parâmetros de URL comuns;3. Extração de arquivos JS para endpoints de API com UUIDs e parâmetros comuns;\
PS: o recon de IDORs pode chegar a ser difícil, devem ser encontrados manualmente usando lógica e dependem muito de cada aplicação. Vá além de testar os parâmetros na URL e também teste com modificações em atributos do objeto JSON.\
Talvez a aplicação tenha controle p/ evitar IDORs em requests com verbos GET, tente explorar em POST, PUT, PATCH e DELETE.

***

JSON Parameter Pollution\
`{“id”:111} --> 401 Unauthriozied`

`{“id”:{“id”:111}} --> 200 OK`

***

#### Generic Trick

#### &#x20;POST /api/get\_profile

#### Content-Type: application/json {“user\_id”:\<attacker\_id>,”user\_id”:\<victim’s\_id>}<br>

***

**HTTP Parameter Pollution**

\
GET /api\_v1/messages?user\_id=VICTIM\_ID --> 401GET /api\_v1/messages?user\_id=attack\&user\_id=VICTIM --> 200 OK<br>

***

JSON Interoperability\
[https://bishopfox.com/blog/json-interoperability-vulnerabilities](https://bishopfox.com/blog/json-interoperability-vulnerabilities)
