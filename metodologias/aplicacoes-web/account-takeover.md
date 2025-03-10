---
hidden: true
---

# Account Takeover

A vulnerabilidade de **Account Takeover** se remete a quando um atacante consegue aproveitar de algum fluxo vulnerável para obter acesso a contas as quais o mesmo não poderia ter acesso.



É sempre interessante analisar os endpoints dos campos de Esqueci a senha, Criar conta, pois os mesmo podem ser vulneráveis a ataques de Account Takeover.



**Pontos para se atentar:**



Um ponto a se observar é qual o **endpoint** que faz a criação do novo usuário, com ele podemos comparar a outras funções dentro da aplicação como a de alterar informações de usuário, caso forem o mesmo endpoint, pode-se testar inserir dados válidos dentro da requisição para avaliar como a aplicação responde.

Verificar se existe **token** neste ponto, caso não haver um token, um atacante pode aproveitar para realizar as ações não autorizadas e por não haver a existência de um token suas ações serão aceitas pela aplicação.



Verificar o mecanismo de **Esqueci a senha**, em alguns casos pode ocorrer falhas lógicas resultando em account takeover, como por exemplo ao interceptar a requisição podemos adicionar mais um e-mail dentro do solicitado de esqueci a senha, o payload pode ser como a seguir:

```
{"email":["vitima@gmail.com","seuemail@gmail.com"]}
```

Em alguns casos, pode ocorrer de ambos os endereços receberem o e-mail de alteração de senha, o que pode ocorrer de um atacante alterar a senha do e-mail da vítima.



**XSS para Account Takeover** - em alguns casos em que a aplicação possua a vulnerabilidade de xss, pode utilizar o payload para capturar cookies dentro da aplicação, com os cookies capturados é possível logar como o usuário dos cookies que foram capturados.\




