---
hidden: true
---

# Controle de Conta via Desvio de Limite de Taxa

Em um programa privado de bug bounty, quando uma redefinição de senha era iniciada, os usuários eram obrigados a inserir um `código numérico de seis dígitos` enviado para seu e-mail para verificação.

Para evitar `ataques de força bruta`, o aplicativo implementou proteção de `limite de taxa`, restringir o número de solicitações que os usuários podem fazer dentro de um prazo específico. Se esse limite fosse superado, o sistema emitiu uma mensagem de erro `"429 Too Many Requests."`

No entanto, a proteção de limite de taxa foi contornada pela adição de dois cabeçalhos `X-Forwarded-For: IP.`



```
POST /reset HTTP/2
Host: example. com
X-Forwarded-For: 1.1.1.1
X-Forwarded-For: 2.2.2.2
```



Ao substituir o endereço IP no segundo cabeçalho `X-Forwarded-For`, tornou-se possível ignorar o `limite de taxa` e tentar vários códigos até que o correto seja encontrado.

A exploração desta vulnerabilidade permitiu o controle não autorizado de qualquer conta dentro do aplicativo.
