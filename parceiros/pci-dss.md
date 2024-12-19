# PCI DSS

Se você contratou a Vantico para um teste de penetração PCI DSS, haverá algumas pequenas diferenças em comparação ao nosso processo regular de teste de penetração. Os objetivos principais do teste de penetração PCI DSS são:

* Valide se o ambiente de dados do titular do cartão (CDE) é isolado, seguro e compatível com os padrões PCI DSS.
* Garanta que os dados do titular do cartão (CHD) estejam protegidos contra acesso não autorizado.
* Identifique e corrija vulnerabilidades que possam comprometer os dados do titular do cartão.

Como resultado, os seguintes processos serão ligeiramente diferentes:

* O escopo do teste de intrusão.
* A documentação antes do teste de penetração do aplicativo PCI DSS.
* A frequência dos testes de intrusão.



## Escopo de um teste de intrusão de aplicativo PCI DSS:

Durante a chamada de escopo, além dos pontos já mencionados, os seguintes aspectos também serão considerados para um teste de intrusão de aplicativo PCI DDS:

* **Teste de Segurança de Aplicação**
  * Teste todos os aplicativos dentro do CDE que lidam com CHD para identificar vulnerabilidades de segurança, incluindo aqueles que aderem aos padrões OWASP. Isso envolve avaliar ameaças comuns, como injeção de SQL, Cross-Site Scripting (XSS), vulnerabilidades de autenticação e falhas de autorização.
* **Teste Aplicação Externa**
  * Simule ataques em aplicativos acessíveis externamente que fornecem acesso ou protegem CHD. Testes externos verificam a segurança de aplicativos voltados para a internet identificando configurações incorretas, portas expostas e vulnerabilidades de acesso externo.
* **Teste Aplicação Interna**
  * Realize avaliações em aplicativos acessíveis de dentro da rede interna. Isso envolve testes de acesso não autorizado, escalonamento de privilégios e riscos potenciais de movimentação lateral se um usuário obtiver acesso não autorizado ao CDE.
* **Teste de Segmentação**
  * Confirme se a segmentação de rede isola efetivamente os aplicativos relacionados ao CHD do restante do ambiente, minimizando o escopo do PCI.











