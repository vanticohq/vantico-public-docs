---
description: >-
  Neste guia, discutiremos como realizamos o escopo e as perguntas que você deve
  fazer a clientes em potencial para ter uma ideia melhor do tamanho de um
  projeto.
---

# Parceiros

**Documentos de suporte:**

* Precificação em excel

**Antes de começarmos**&#x20;

Algumas coisas importantes para lembrar durante o escopo:&#x20;

Não é uma ciência exata. Muitas vezes, estamos estimando com base na experiência passada e nos dados limitados fornecidos a nós pelos clientes.&#x20;

Dado o ponto 1, não há problema em sub/superdimensionar o escopo. Erros acontecerão; não há necessidade de se estressar com isso. Aprenda e siga em frente.&#x20;

É mais fácil obter informações de um cliente em uma chamada de escopo de 30 minutos do que em um documento de escopo. Geralmente, com a cultura da nossa empresa, preferimos a comunicação pessoal, mas também é mais fácil fazer perguntas diretas sobre o escopo e os porquês.&#x20;

O escopo deve ser fácil para o cliente. As perguntas sobre o escopo podem ser incomuns para eles. Tente tornar a experiência o mais fácil possível.&#x20;

A estimativa de tempo deve incluir tudo o que é necessário para fornecer um serviço de alta qualidade. Isso inclui:&#x20;

* O hacking/teste/trabalho/etc. real.&#x20;
* Escrita de relatório&#x20;
* QA desse relatório&#x20;
* Reuniões de início e debriefing&#x20;
* Comunicações contínuas com o cliente&#x20;
* Tempo de viagem interestadual&#x20;

Com esses pontos em mente, vamos continuar.



Normalmente, a conversa pode começar com um cliente pedindo um trabalho muito específico: "Preciso de um teste de invasão externo". &#x20;

Esse é um ótimo ponto de partida, mas precisamos dar alguns passos para trás. &#x20;

* Por que eles precisam de um teste de invasão externo? &#x20;

Pesquise profundamente aqui. Respostas como "Para encontrar vulnerabilidades" não são úteis, então você terá que ser mais direto. &#x20;

* Existe um requisito de auditoria? &#x20;
* Eles estão preocupados que os dados do cliente sejam violados?&#x20;
* Eles têm um programa de segurança? &#x20;
* Existe um requisito de tempo do teste? &#x20;

Diferentes empresas se preocupam com a segurança por diferentes motivos, e é importante chegar ao cerne desses motivos.&#x20;

Entender os motivos ajudará imensamente ao recomendar o que eles devem fazer com sua segurança. Talvez um teste de invasão externo seja o caminho certo a seguir, mas talvez uma revisão de segurança seja melhor, ou ambos.&#x20;

**Perguntas de contexto**&#x20;

Algumas outras coisas que você pode querer perguntar:&#x20;

* **Prazos**: quando eles precisam que o trabalho comece? Há algum prazo?&#x20;
* **Orçamento**: é totalmente aceitável se o cliente não tiver um e não quiser compartilhar essas informações, mas saber o orçamento nos ajuda a fazer melhores recomendações e obter o melhor retorno sobre o investimento.&#x20;
* **Restrições**: há algo que possa afetar nossa capacidade de fazer o trabalho?&#x20;
* **Comunicação**: eles preferem e-mail ou reuniões?

**Escopo do teste de invasão** &#x20;

Agora que você conhece os requisitos do cliente e por que ele precisa de ajuda com infosec, podemos fazer perguntas específicas sobre o escopo pretendido.&#x20;

(Se ainda não fez, agora é um bom momento para fazer uma pausa e verificar nosso Catálogo de Serviços antes de continuar) .

<mark style="color:blue;">**Teste de Invasão externo**</mark>&#x20;

Este é bem fácil. Usamos números brutos para isso, então precisamos saber:&#x20;

* Quantos endereços IP externos o cliente possui (total)?&#x20;
* Quantos deles estão ativos (hospedando pelo menos 1 serviço)?&#x20;
* Quantos domínios raiz estão no escopo (por exemplo, example.com)?&#x20;

Uma coisa importante a ser observada: os testes de invasão externos cobrem aplicativos prontos para uso, como Outlook Web Access, páginas de login VPN, compartilhamento de arquivos etc., mas não cobrem aplicativos da Web personalizados criados apenas para o cliente. Use o guia de escopo do aplicativo da Web para eles.&#x20;

<mark style="color:blue;">**Teste de invasão interno**</mark>&#x20;

Os internos são muito parecidos. Usamos números brutos para determinar o tamanho do escopo:&#x20;

* Quantos servidores existem (físicos e virtuais)?&#x20;
* Quantos dispositivos de rede existem (roteadores, switches, pontos de acesso etc.)?&#x20;
* Quantos dispositivos de usuário existem (estações de trabalho, laptops)?&#x20;
* Quantos dispositivos de IoT existem (câmeras, telefones, impressoras, qualquer outra coisa com um endereço IP)?&#x20;
* Existe um domínio do Windows (Active Directory)?&#x20;
* De qual local físico estamos testando?&#x20;

<mark style="color:blue;">**Teste de invasão de Aplicação Web**</mark>&#x20;

Devido à complexidade dos aplicativos da Web, eles podem ser incrivelmente difíceis de definir. Em vez de usar números brutos como nos anteriores, tentamos avaliar o quão "complexo" um aplicativo da Web é. Normalmente, quanto mais funções, mais complexo o aplicativo é. Se alguma funcionalidade afeta outra funcionalidade, a complexidade aumenta novamente.&#x20;

* Em média quantas páginas existem na aplicação?
* A aplicação consome API?
* Quantos Perfis de Usuários seriam testados?

**Autenticado vs. Não autenticado**&#x20;

Autenticado vs. Não autenticado é tudo sobre a perspectiva. Quantas funções podem ser vistas/acessadas da perspectiva fornecida. A perspectiva guiará o tamanho visível do aplicativo. Por exemplo, um aplicativo CMS visto de uma perspectiva autenticada teria centenas de funções, tornando-o uma aplicação grande. Enquanto isso, o mesmo aplicativo de uma perspectiva não autenticada teria apenas as funções de login e redefinição de senha visíveis, tornando-o uma aplicação pequena.&#x20;

&#x20;<mark style="color:blue;">**Teste de invasão de aplicação mobile**</mark>&#x20;

Aplicativos móveis são tão complexos de escopo quanto aplicação web.&#x20;

* Este aplicativo está no Android, iOS ou ambos?&#x20;
* Como podemos obter acesso ao aplicativo (por exemplo, AppStore, TestFlight, arquivo apk personalizado)?&#x20;
* Em média quantas telas existem no aplicativo?

&#x20;<mark style="color:blue;">**Campanha de phishing**</mark>&#x20;

O phishing é mais bem discutido com o cliente por meio de uma chamada. No entanto, algumas perguntas preliminares são:&#x20;

* Quantos usuários estamos testando?&#x20;
* Quantas campanhas (rodadas) estamos realizando?&#x20;

Outros serviços&#x20;

Qualquer serviço não coberto acima deve ter uma chamada de escopo. Como a infosec é cheia de jargões e terminologia mista, há muito espaço para confusão sem uma chamada de escopo.

**Projetos com tempo limitado**&#x20;

Embora prefiramos projetos de escopo completo (cujo fim é ditado por um resultado), oferecemos uma opção para limitar o tempo de um projeto.&#x20;

Em um projeto com tempo limitado (ou time-boxed), realizamos qualquer trabalho que pudermos em um determinado período de tempo. Nesse cenário, não podemos garantir um resultado satisfatório ou que cobrimos todo o escopo, e é por isso que não é o ideal.&#x20;

Há, no entanto, circunstâncias em que um projeto com tempo limitado é favorável; por exemplo, quando o escopo não é bem definido devido à falta de informações, ou quando há restrições de tempo ou orçamento.&#x20;

<mark style="color:blue;">**Custos de viagem**</mark>&#x20;

Alguns trabalhos, como testes de invasão internos, exigem que compareçamos ao escritório do cliente e o local específico do teste deve ser discutido com o cliente durante o escopo. Isso significa que pode haver custos de viagem se o consultor precisar viajar para um local de difícil acesso.&#x20;

Os custos de viagem devem ser estimados com antecedência e adicionados ao orçamento total do projeto. Eles são cobrados pelo custo, portanto, não obtemos lucro aqui. Os custos de viagem podem incluir:&#x20;

* Voos&#x20;
* Acomodação&#x20;
* Transfers de/para o aeroporto&#x20;
* Aluguel de carro&#x20;
* Refeições&#x20;

&#x20;<mark style="color:blue;">**Dúvidas?**</mark>&#x20;

A segurança é um problema complicado, então, se você tiver alguma dúvida, nossos consultores estão sempre disponíveis para respondê-las ou atender chamadas de escopo com os clientes.&#x20;
