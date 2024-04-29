---
description: >-
  Revise as metodologias de pentest do Vantico para redes externas (inclui
  instâncias do Microsoft Office 365).
---

# Metodologias de Rede Externa

O teste de penetração de rede externa é um processo no qual um testador usa ataques simulados para identificar possíveis vulnerabilidades de segurança em uma rede externa.



Seguimos uma metodologia padrão do setor baseada principalmente no Manual de Metodologia de Teste de Segurança de Código Aberto (OSSTMM).

<figure><img src="../../.gitbook/assets/rede externa.png" alt=""><figcaption></figcaption></figure>

O teste de penetração de uma rede externa inclui as seguintes etapas:

* Reconhecimento de escopo alvo
* Descoberta de serviço
* Verificações de vulnerabilidade
* Avaliação manual
* Testes adicionais
* Relatórios, triagem e re-tests

Ao testar instâncias do Microsoft Office 365, os pentesters analisam a segurança e a criptografia dos dados e verificam os controles de acesso, além de testar a rede que hospeda os serviços que estão no escopo.



> Nota:\
> As ferramentas que nossos pentesters usam durante cada fase de teste podem variar de teste para teste.



A equipe de avaliação de segurança da Vantico realiza testes sem o seguinte, a menos que seja exigido como parte do escopo do pentest:

* Diagramas detalhados de rede ou infraestrutura
* Quaisquer contas ou informações adicionais do usuário

No entanto, você pode adicionar diagramas de rede e outros detalhes ao descrever seu ativo.



**Reconhecimento do Escopo Alvo**

Os pentesters Vantico procuram todas as informações que um usuário mal-intencionado possa encontrar. Por exemplo, para se conectar à Internet, você normalmente compartilha algumas informações:

* Para receber e-mail, você precisa postar um endereço de servidor de e-mail.
* Para configurar um servidor web, você precisa postar seu URL e muito mais.

Durante a fase inicial de testes, os pentesters determinam quais informações estão disponíveis publicamente. Eles examinam o seguinte:

* **Seu site corporativo**. Os pentesters da Vantico avaliam seu site de maneiras que podem interessar a um invasor em potencial, incluindo:
  * Locais (URL)
  * Detalhes de contato, como números de telefone, e-mails ou endereços físicos
  * Informações de domínio
  * Links para outros servidores dentro de uma organização
  * Outras empresas com links para o seu site
  * Informações sobre a política de segurança da sua organização
* **Outros locais da web e bancos de dados.** Os pentesters do Vantico procuram informações sobre seus ativos em outros sites e bancos de dados, especialmente qualquer coisa relacionada a empresas de capital aberto. Os pentesters então avaliam quais informações a organização torna públicas, especialmente qualquer coisa que vá além do exigido pelas leis locais. Eles também avaliam artigos de notícias e comunicados de imprensa em busca de mais pistas sobre sua política de segurança.
* **Seus nomes de domínio.** Os pentesters Vantico usam bancos de dados “whois” para identificar os domínios que você possui. Esses domínios fornecem informações sobre sua infraestrutura de rede.
* **Dados públicos**. Os registros públicos sobre sua organização podem incluir informações sobre as pessoas responsáveis pela administração do seu domínio, como nome, endereço ou número de telefone. Os invasores podem usar engenharia social para obter informações adicionais, como detalhes de compras de hardware e software. Também fornece pistas sobre onde pode ser o melhor local para direcionar um ataque.



**Ferramentas:**

Durante esta fase de testes, os pentesters usam várias ferramentas, como:

* Nmap
* DirBuster
* Shodan
* Censys

Com essas ferramentas, os pentesters podem encontrar:

* Endereços IP
* Redes
* Portas abertas
* Webcams
* Impressoras
* Outros dispositivos conectados à internet

Com essas informações, nossos pentesters podem identificar potenciais pontos fracos, como:

* Vazamentos acidentais de informações confidenciais
* Abrir portas de rede
* Dispositivos de rede inseguros
* Software sem patch
* Ativos vazados ou expostos em pastebins



**Descoberta de serviço**

Depois de reunir todas as informações disponíveis, nossos pentesters investigam os recursos pertencentes à organização visada. Esses testes envolvem várias etapas:

* Varreduras de portas&#x20;
* Investigação aprofundada



**Ferramentas:**

Durante esta fase de testes, os pentesters usam várias ferramentas, como:

* Nmap
* Aquatone
* EyeWitness
* testssl.sh



Como certas vulnerabilidades e explorações podem paralisar, danificar ou alterar o conteúdo da rede, nossos pentesters não realizam esses ataques. Eles anotam os possíveis riscos. Por exemplo, nossos pentesters não executarão explorações que:

* Desative certos serviços
* Negar serviço de sistemas externos
* Pode afetar os clientes (como um ataque de negação de serviço (DoS))
* Desabilitar a capacidade de funcionamento de uma organização



**Varreduras de portas**

Os pentesters realizam uma varredura completa de portas nos intervalos de endereços IP do seu ativo. A partir dessas informações, os pentesters podem identificar máquinas e recursos voltados ao público, juntamente com suas funcionalidades.

Por exemplo, os seguintes serviços requerem acesso ao mundo exterior para funcionar:

* Firewalls
* Servidores de e-mails
* Servidores Office 365
* Servidores web
* Servidores FTP

Todos esses serviços deixam assinaturas características que uma varredura de porta pode detectar.



**Investigação aprofundada**

Com base nos resultados da verificação inicial da porta, nossos pentesters trabalham para identificar:

* Os tipos de aplicativos executados em máquinas expostas externamente
* Números de versão do software identificado
* Sistemas operacionais nos quais o software é executado

Em alguns casos, uma máquina exposta externamente pode ter serviços abertos que não possuem funções associadas a eles. Os pentesters podem identificá-los e direcioná-los para testes.



**Verificações de vulnerabilidade**

Os pentesters Vantico fazem o acompanhamento identificando vulnerabilidades na parte externa da rede. Seu objetivo é penetrar em endpoints externos e obter acesso à LAN interna e aos recursos da organização.

Se um potencial invasor atingir esse objetivo, uma organização poderá enfrentar:

* Vazamentos de informações sensíveis ou confidenciais da rede da organização. A exfiltração de segredos comerciais ou dados de comunicação interna pode prejudicar a organização afetada. Esses vazamentos podem incluir:
  * Registros de pessoal
  * Dados de pagamento
  * Outros registros financeiros
* Atacantes que usam o gateway de e-mail ou site como fonte de e-mail de spam. Outros sites podem colocar o domínio da organização na lista negra e rejeitar automaticamente correspondências de e-mail legítimas.
* Interrupções de serviço, a ponto de os recursos da organização ficarem indisponíveis, temporária ou permanentemente.
* Desfiguração do site. Os invasores podem até mesmo substituir sua própria versão do site onde os clientes atuais ou potenciais fazem login. A organização pode perder credibilidade ou até mesmo clientes em potencial.



**Ferramentas:**

Durante esta fase de testes, os pentesters usam várias ferramentas, como:

* Metasploit
* Nessus
* Nmap
* Burp Suite Community/Professional
* Nikto



**Avaliação Manual**

Durante a avaliação manual, os pentesters da Vantico examinam os recursos específicos que identificaram. Na maioria dos casos, os pentesters se concentram em serviços visivelmente abertos:

* Servidores web
* Servidores FTP
* Servidores de e-mail
* Firewalls
* Roteadores
* Servidores DNS
* Outros serviços existentes no intervalo de endereços IP externos, incluindo serviços do Office 365



Embora os pentesters realizem verificações com base nas especificidades de uma determinada situação, um cenário comum envolve examinar o seguinte:

* Sistema de Nomes de Domínio (DNS)
* Roteadores
* Firewalls
* Servidores web
* Servidores de e-mail
* Sites remotos e redes privadas virtuais
* Verificando o uso de versões seguras
* Garantindo a segurança de protocolos legados



**Ferramentas:**

Durante esta fase de testes, os pentesters usam várias ferramentas, como:

* Burp Suite Community/Professional
* Metasploit
* sqlmap
* Postman



**Sistema de Nomes de Domínio (DNS)**

Para que as organizações usem a Internet, os usuários da rede precisam ter a capacidade de consultar servidores DNS. Algumas organizações possuem seu próprio servidor DNS e algumas dependem de servidores DNS externos. Se o servidor DNS interno de uma organização falhar, isso poderá causar a queda da conexão com a Internet.

Os invasores também podem obter conhecimento interno de um servidor DNS, como:

* Como o domínio envia e recebe e-mail&#x20;
* Locais do site

Vejamos um exemplo de erro grave de configuração de DNS que pode ocorrer. Quando uma organização permite que usuários desconhecidos da Internet realizem uma transferência de zona DNS, um invasor pode obter acesso a informações valiosas sobre a rede



**Roteadores**

Todas as conexões com a Internet normalmente passam por um roteador de fronteira gerenciado pelo Provedor de Serviços de Internet (ISP). No entanto, às vezes os roteadores permanecem sem correção por um longo período ou as contas de usuário padrão permanecem ativas.

Localizamos todos os roteadores visíveis, estabelecemos o fabricante e o sistema operacional (SO) e, em seguida, verificamos possíveis vulnerabilidades. Nossos testes incluem:

* Verificando o software para garantir que seus roteadores estejam corrigidos e atualizados&#x20;
* Contas de usuário padrão, como admin&#x20;
* Tentativas de acessar o roteador usando vários bancos de dados de senhas e configurações padrão conhecidas



**Firewalls**

Um firewall foi projetado para ser a principal porta de entrada de uma organização, com regras para proteger os recursos internos. Um invasor pode obter acesso à tecnologia de firewall, por isso não recomendamos tratá-la como uma solução “pronta para uso”. Uma organização deve configurar um firewall para as necessidades específicas de seus negócios e mantê-lo atualizado por meio de patches e manutenção.

Nossos pentesters procuram erros de configuração que possam deixar um caminho para a LAN corporativa. Os pentesters tentam realizar ataques de firewall, como:

* Estouros de buffer&#x20;
* Falsificação de IP&#x20;
* Pacotes IP corrompidos&#x20;
* Ataques contra serviços abertos



**Servidores Web**

Os servidores Web são vulneráveis a ataques de desfiguração ou podem ser usados como plataforma de lançamento para novos ataques contra redes internas.

Os pentesters Vantico verificam todos os servidores web (lado do cliente) em busca de possíveis explorações e vulnerabilidades, como:

* Política de patch ruim&#x20;
* Instalação padrão



**Servidores de E-mail**

Os pentesters Vantico verificam SMTP, POP3 e IMAP no gateway de e-mail em busca de vulnerabilidades de retransmissão aberta. Seus servidores de e-mail devem:

* Aceitar e-mails _apenas_ para os domínios da organização&#x20;
* Não retransmitir e-mails para outros domínios

Os invasores podem explorar uma retransmissão aberta para inundar o servidor de e-mail com spam, o que pode levar o domínio à lista negra.

Os pentesters examinam o servidor de e-mail usando vários métodos, como enviar e-mails para domínios inexistentes.



**Sites remotos e rede privada virtual (VPN)**

As infraestruturas de rede corporativa podem exigir conexões com vários outros escritórios subsidiários em todo o mundo através de uma VPN. Embora as VPNs suportem comunicação segura, elas podem ser vulneráveis aos mesmos problemas de configuração que os firewalls, porque os firewalls controlam a VPN.

Uma VPN configurada incorretamente para um site subsidiário pode ser um vetor de ataque à rede corporativa principal.



**Verificando o uso de versões seguras**

À medida que os pesquisadores descobrem vulnerabilidades e falhas de segurança no software, os fornecedores de software lançam patches para seus produtos. Nossos pentesters procuram versões de software desatualizadas e sem correção. Eles executam testes contra explorações publicadas e corrigidas.

Versões mais antigas têm limites de segurança mais baixos e deixam os dados vulneráveis. De acordo com o SANS Institute, algumas das vulnerabilidades mais comuns são baseadas em versões desatualizadas do Office 365. Vantico pode realizar pentests para instâncias do Office 365.



**Garantindo a segurança de protocolos legados**

Os pentesters Vantico podem testar protocolos legados, como POP3, IMAP e SMTP, em busca de vulnerabilidades conhecidas. Eles verificam se o uso desses protocolos está protegido contra falhas de segurança documentadas



**Testes Adicionais**

Os pentesters Vantico usam várias ferramentas personalizadas e disponíveis publicamente durante um pentest, como:

* Port Scanners
* Verificadores de vulnerabilidade automatizados&#x20;
* Proxies HTTP&#x20;
* Explorações&#x20;
* Scripts personalizados&#x20;
* Aplicativos de segurança



**Relatórios, triagem e re-test**

Os pentesters Vantico relatam e fazem a triagem de todas as vulnerabilidades durante a avaliação. Você pode revisar os detalhes de todas as descobertas, em tempo real, por meio da plataforma Vantico. Nessas descobertas, assim como em qualquer relatório, nossos pentesters incluem informações detalhadas sobre como você pode:

* Corrigir cada descoberta&#x20;
* Melhorar sua postura geral de segurança

Você pode corrigir as descobertas durante e após o pentest. Em seguida, você pode enviar as descobertas para novo teste. Nossos pentesters testam os componentes atualizados e testam novamente os problemas para garantir que não haja riscos residuais relacionados à segurança.

