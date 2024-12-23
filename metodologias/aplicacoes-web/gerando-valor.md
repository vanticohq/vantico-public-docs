# Gerando Valor

### Possibilidade de manipular comandos SQL na aplicação

Após explorar a vulnerabilidade de SQL Injection, podemos explorar ainda mais dentro da aplicação consultando se há a presença de seguintes vulnerabilidades, como:&#x20;

**Verificação de presença de salt:**

* Validar se dentro da criptografia, a mesma possui salt implementado como forma de tornar mais seguro o hash.

**Permissão do usuário:**

* Deve ser validado se o usuário utilizado para a exploração possui acesso a todos os bancos de dados, a boa prática é cada usuário somente ter acesso ao banco que utiliza, com o intuito de que caso uma exploração ser bem sucedida, o atacante remoto não consiga comprometer mais ambientes.

**Senhas em texto plano:**

* Ao conseguir o acesso, deve ser validado a maneira como as senhas estão sendo armazenadas, caso as senhas se encontrem em texto plano deve ser reportado.



***





