# Controle de Conta via Desvio de Limite de Taxa

Em um programa privado de bug bounty, quando uma redefinição de senha era iniciada, os usuários eram obrigados a inserir um <mark style="color:red;background-color:purple;">código numérico de seis dígitos</mark> enviado para seu e-mail para verificação.

Para evitar <mark style="color:red;background-color:purple;">ataques de força bruta</mark>, o aplicativo implementou proteção de <mark style="color:red;background-color:purple;">limite de taxa</mark>, restringir o número de solicitações que os usuários podem fazer dentro de um prazo específico. Se esse limite fosse superado, o sistema emitiu uma mensagem de erro <mark style="color:red;background-color:purple;">"429 Too Many Requests."</mark>

No entanto, a proteção de limite de taxa foi contornada pela adição de dois cabeçalhos <mark style="color:red;background-color:purple;">X-Forwarded-For: IP.</mark>



```
POST /reset HTTP/2
Host: example. com
X-Forwarded-For: 1.1.1.1
X-Forwarded-For: 2.2.2.2
```



Ao substituir o endereço IP no segundo cabeçalho <mark style="color:red;background-color:purple;">X-Forwarded-For</mark>, tornou-se possível ignorar o <mark style="color:red;background-color:purple;">limite de taxa</mark> e tentar vários códigos até que o correto seja encontrado.

A exploração desta vulnerabilidade permitiu o controle não autorizado de qualquer conta dentro do aplicativo.
