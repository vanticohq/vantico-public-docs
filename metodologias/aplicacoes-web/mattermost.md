# Mattermost

Mattermost é uma aplicação open source de bate-papo muito utilizada por organizações e empresas, ela se torna uma alternativa entre o Microsoft Teams e o Slack.



Em um pentest realizado, foi encontrado algumas vulnerabilidades na empresa que utilizava-se esta aplicação desatualizada.

Quando acessado o link de acesso ao bate-papo, de imediato não temos acesso ao grupos pois apenas quem é invitado pode participar e visualizar o conjunto,

Entretanto, quando interceptamos essa requisição com o Burp Suite, podemos visualizar que usualmente a requisição se faz por:

```
GET /api/v4/users/me/groups
```

Quando enviado ao repeater, podemos trocar essa requisição para:

```
GET /api/v4/users
```

Assim, conseguimos listar todos os usuários que utilizam o Mattermost, exibindo seus IDs, nome completo, nickname, email, data de criação da conta, cargo, entre outras informações, tornando assim possível um atacante enumerar todos os usuários e utilizar um ataque de força bruta para tentar acessar a conta do usuário.



Sendo assim, devemos sempre manter nossas dependências atualizadas para evitar de que vulnerabilidades presentes em versões anteriores afetem a operação da empresa.
