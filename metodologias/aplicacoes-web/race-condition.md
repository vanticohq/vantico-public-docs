---
hidden: true
---

# Race Condition

O principal problema de explorar Race Conditions é que você precisa que as solicitações sejam processadas em paralelo com uma diferença de tempo muito curta (geralmente >1ms). A versão 2023.9 do Burp Suite introduz uma nova função no Burp Repeater, focada em aprimorar a capacidade de enviar solicitações em paralelo com um impacto reduzido do jitter de rede. Onde o jitter de rede pode afetar negativamente a sincronização de solicitações.

\
O HTTP2 permite enviar 2 solicitações em uma única conexão TCP, enquanto em HTTP/1.1 elas precisam ser sequenciais. Então, o uso de um único pacote TCP elimina completamente completamente o efeito do jitter.

\
A base da exploração de um Race Condition consiste em múltiplos threads interagindo com o mesmo dado ao mesmo tempo, resultando em um tipo de "colisão" que causa um comportamento inesperado. O tipo mais conhecido de Race Condition é exceder algum tipo de limite imposto pela lógica da aplicação.

\
Hoje em dia a aplicação raramente é elaborada tendo em mente os riscos de simultaneidade e como resultado, Race Conditions acaba sendo uma vulnerabilidade presente na maioria dos sistemas.

\
Os exploits na maioria das vezes se baseiam na ultrapassagem de limite, por exemplo:

* Utilização de gift cards múltiplas vezes
* Aplicação de cupons múltiplas vezes
* Convidar a mesma pessoa múltiplas vezes
  * Verifique como a aplicação se comporta
  * Caso funcione, exclua um usuário
  * Verifique se o usuário persiste no projeto
* Ultrapassar o limite imposto por um determinado plano de usuário (e.g. plano Básico x Pro)

\
A causa de todos eles é semelhante. Todos exploram o intervalo de tempo entre a verificação de segurança e a ação. Por exemplo, dois threads podem consultar simultaneamente um banco de dados e confirmar que o código de desconto LESIS10 não foi aplicado ao carrinho, então ambos tentam aplicar o desconto, resultando na aplicação do mesmo duas vezes.

\
Com isso, você pode optar por testar qualquer função na aplicação que você ache passivo de sofrer de um Race Condition e que tenha um impacto significativo.

\
Caso tenha dúvidas em relação ao envio de múltiplas requisições com o Burp Repeater, leia: [Sending grouped HTTP requests](https://portswigger.net/burp/documentation/desktop/tools/repeater/send-group#sending-requests-in-parallel)

\
Caso ainda tenha duvidas de como a exploração funciona, teste os laboratórios da PortSwigger abordando o assunto e leia o writeup do desafio web do Hack The Box "Diogenes Rage":

* [drt.sh - HTB Diogenes Rage Writeup](https://drt.sh/posts/htb-diogenes-rage/)
* [PortSwigger Labs - Race Conditions](https://portswigger.net/web-security/all-labs#race-conditions)

\
Referências

* [PortSwigger - Race Conditions](https://portswigger.net/web-security/race-conditions)
* [PortSwigger Research - Smashing the state machine](https://portswigger.net/research/smashing-the-state-machine)
* [PortSwigger Research - Cracking reCAPTCHA, Turbo Intruder style](https://portswigger.net/research/cracking-recaptcha-turbo-intruder-style)
