---
description: Um destino é o URL de um aplicativo Web, site ou API.
---

# Alvos

{% hint style="info" %}
Um alvo define o escopo da verificação.
{% endhint %}



O que é um alvo DAST?

Um alvo ADAST é o ponto de entrada específico (URL ou endpoint) de um aplicativo web, site, API ou qualquer componente que aceite entrada do mundo externo. Ele define o escopo, ou limites, da verificação de segurança conduzida por uma ferramenta DAST, limitando a ferramenta a analisar apenas as páginas, links ou formulários dentro do domínio do alvo.

Por exemplo, com um destino https://example.com, a verificação cobriria https://example.com/app1, mas não https://app2.example.com. Essencialmente, o scanner examina URLs que começam com “example.com”.



**Exemplos de alvos DAST:**

* **URLs**: estes são os alvos mais comuns, representando páginas da web ou seções individuais dentro de um aplicativo:
  * _https://www.example.com:_ domínio de nível superior que hospeda o aplicativo
  * _https://example.com/blog_: subpasta ou subseção dentro do aplicativo
  * _https://admin.example.com_: subdomínio que hospeda um aplicativo separado
* **APIs**: os aplicativos geralmente usam APIs para comunicação, e o DAST pode identificar vulnerabilidades como acesso não autorizado ou vazamento de dados:
  * _https://api.us.example.com_: API interna hospedada em um subdomínio
  * _https://api.eu.example.com:_ instância de API separada hospedada de forma independente
* **Formulários**: o DAST pode avaliar a segurança de formulários de login, páginas de registro e outros campos de entrada contra ataques como injeção de SQL ou scripts entre sites:
  * _https://example.com/login_: formulário de login no domínio de nível superior
  * _https://checkout.example.com_: formulário de checkout e pagamento hospedado em um subdomínio



**O que NÃO é um alvo DAST:**

* **Ativos Vantico**: Ativos no Vantico não são sinônimos de metas. Um ativo geralmente é um aplicativo inteiro, composto por vários sistemas internos e de terceiros, APIs e outros componentes. As ferramentas DAST não analisam uma base de código inteira, mas concentram-se apenas nas partes que aceitam entradas externas. Esses componentes, que residem em um URL exclusivo (ou seja, _exemplo.com, app.example.com e api.example.com_), constituiriam, cada um, um alvo individual.
* **Servidores ou redes**: embora os aplicativos sejam executados em servidores e interajam com redes, as ferramentas DAST normalmente não testam diretamente esses aspectos.
* **Código fonte:** o DAST analisa o comportamento do aplicativo, não o código em si. Esse é o domínio do Static Application Security Testing (SAST).
* **Aplicativos de terceiros**: aplicativos externos nos quais os clientes não têm aprovação para executar verificações ou testes.

Um alvo DAST claro e bem definido garante que a verificação se concentre nas áreas específicas de um aplicativo mais suscetíveis a ameaças externas.





**Configurando um alvo**

Existem algumas opções de configuração disponíveis ao configurar alvos.

* **Destinos autenticados**: você pode ver uma explicação detalhada em Autenticação.
* **URLs evitados**: as verificações funcionam rastreando e descobrindo novos URLs em seu aplicativo. Se quiser reduzir o escopo da verificação para evitar a verificação de determinadas partes do aplicativo, você pode adicioná-las aos URLs evitados. Estes são exemplos válidos para URLs evitados:

```
https://example.com/admin*
https://api.example.com/api/users*
https://example.com/account*
```

**Caminhos iniciais**: de maneira semelhante, uma varredura geralmente começa a partir do URL de destino. Às vezes, existem algumas páginas que não podem ser acessadas a partir daí. Se quiser adicionar alguns pontos de partida extras para a varredura, você pode usar caminhos iniciais. Observe que apenas caminhos relativos são permitidos e os URLs evitados têm precedência. Este é um exemplo válido:

```
posts/search?query=vantico
```

