# Ferramentas

Na Vantico, adotamos uma seleção rigorosa das ferramentas de segurança mais avançadas e atualizadas para conduzir nossos testes de intrusão. Além disso, complementamos essas soluções tecnológicas com técnicas manuais aplicadas por nossos especialistas altamente qualificados, assegurando uma avaliação abrangente e precisa da segurança da sua infraestrutura.

Abaixo se encontram algumas das ferramentas utilizadas pelos nossos profissionais:

#### [Certipy](https://github.com/ly4k/Certipy)

Uma ferramenta ofensiva para enumerar e abusar dos Serviços de Certificação do Active Directory (AD CS).

**Por que gostamos dela:** Esta ferramenta foi projetada para ajudá-lo a acessar melhor a postura de segurança dos seus ambientes de Serviços de Certificação do Active Directory. Com o Certipy, você pode identificar modelos de certificado vulneráveis que podem ser usados para obter informações sensíveis ou elevar o domínio AD. O Certipy pode extrair credenciais, realizar ataques de credenciais sombra e criar Golden Tickets para privilégios de alto nível para qualquer usuário no domínio.

#### [BloodHound](https://github.com/BloodHoundAD/BloodHound)

Uma aplicação web em Javascript de página única que utiliza teoria dos grafos para revelar as relações ocultas e muitas vezes não intencionais dentro de um ambiente do Active Directory ou Azure.

**Por que gostamos dela:** O BloodHound foi projetado especificamente para visualizar e analisar ambientes do Active Directory ou Azure. Ele mapeia as relações, proporcionando uma visão clara dos caminhos de ataque potenciais que poderiam ser explorados. Se você está procurando uma ferramenta de código aberto que lhe dê a capacidade de identificar fraquezas e ver os movimentos potenciais de um atacante no caso de uma violação, o BloodHound é uma ótima ferramenta para considerar.

#### [Impacket](https://github.com/fortra/impacket)

Uma coleção de classes Python para trabalhar com protocolos de rede.

**Por que gostamos dela:** Uma poderosa biblioteca Python com uma ampla gama de capacidades para profissionais de segurança e pentesters (embora também seja utilizada por atores de ameaça). O Impacket fornece implementações de vários protocolos de rede Windows, permitindo verdadeira versatilidade com sistemas Windows. Alguns dos principais casos de uso incluem quebra de senhas, escalonamento de privilégios, movimentação lateral uma vez na rede e extração de credenciais da memória. O Impacket possui uma forte comunidade de usuários e desenvolvedores, então você pode obter suporte e recursos enquanto o utiliza.

#### [Paramalyzer](https://github.com/PortSwigger/paramalyzer)

Uma extensão do Burp Suite que melhora a eficiência da análise manual de parâmetros para testes de intrusão em aplicações web, sejam elas complexas ou numerosas.

**Por que gostamos dela:** O Paramalyzer é seu propulsor ao realizar a análise manual de aplicações web. O Paramalyzer ajuda a analisar as entradas básicas da aplicação a partir do histórico do proxy e pode identificar dados sensíveis, algoritmos de hash e parâmetros de decodificação.

#### [Hackvertor](https://github.com/hackvertor/hackvertor)

Uma ferramenta de conversão baseada em tags escrita em Java, implementada como uma extensão do Burp Suite.

**Por que gostamos dela:** Outra extensão do Burp Suite, o Hackvertor é uma ótima ferramenta para testes automatizados para identificar vulnerabilidades potenciais, incluindo injeção de SQL, Cross-Site Scripting (XSS), Cross-Site Request Forgery (CSRF), varredura de vulnerabilidades para exploits e vulnerabilidades conhecidas, e testes personalizados para alvos específicos. É uma ferramenta fácil de usar, mas poderosa, bastante flexível para criar testes personalizados e oferece uma automação sólida.

#### [Response-Overview](https://github.com/PortSwigger/response-overview)

Uma ferramenta de conversão baseada em tags escrita em Java, implementada como uma extensão do Burp Suite.

**Por que gostamos dela:** O Response-Overview fornece, como o nome sugere, uma visão detalhada da sua postura de segurança. Ele permite identificar vulnerabilidades, entender o impacto potencial, incluindo perda de dados e interrupções, e priorizar a remediação com base na gravidade, fornecendo orientações. A visão abrangente é um dos principais atrativos desta ferramenta.

#### [CloudFox](https://github.com/BishopFox/cloudfox)

Uma ferramenta de linha de comando criada para ajudar pentesters e outros profissionais de segurança ofensiva a encontrar caminhos de ataque exploráveis na infraestrutura em nuvem.

**Por que gostamos dela:** O CloudFox é uma ferramenta indispensável para pentesters avaliando ambientes de nuvem e o faz de maneira eficiente e eficaz. Ele automatiza muitas das tarefas envolvidas, como enumeração e coleta de credenciais, permitindo que pentesters se concentrem nos aspectos mais complicados de sua avaliação. O CloudFox é versátil e se integra com as principais plataformas de nuvem como AWS, Azure e GCP. Não acredite apenas em nós, pergunte à forte comunidade de usuários ativos que contribuem para o desenvolvimento.

#### [Swagger Jacker](https://github.com/BishopFox/sj)

Swagger Jacker é uma ferramenta de linha de comando projetada para auxiliar na auditoria de arquivos de definição Swagger/OpenAPI expostos, verificando os endpoints de API associados para autenticação fraca.

**Por que gostamos dela:** O Swagger Jacker reduz a tarefa tediosa de auditar endpoints de API, ajudando você a não se sobrecarregar com centenas de rotas definidas e testes manuais que podem estar associados a testes e avaliações de API. Ele avalia vulnerabilidades como ataques de injeção, falhas de autenticação e problemas de autorização.

#### [JSluice](https://github.com/bishopfox/jsluice)

Um pacote Go e uma ferramenta de linha de comando para extrair URLs, caminhos, segredos e outros dados interessantes do código-fonte JavaScript.

**Por que gostamos dela:** O JSluice atua como uma ferramenta poderosa para ajudá-lo a filtrar grandes quantidades de código JavaScript, extraindo informações valiosas de forma eficiente e destacando potenciais vulnerabilidades. Esta ferramenta de mineração de JavaScript vale seu peso em ouro.

#### [OFFAT](https://github.com/OWASP/OFFAT)

A ferramenta OWASP OFFAT avalia autonomamente sua API em busca de vulnerabilidades prevalentes, embora a compatibilidade completa com OAS v3 esteja pendente. O projeto continua em desenvolvimento, evoluindo continuamente em direção à conclusão.

#### [**Spider Foot**](https://github.com/smicallef/spiderfoot)

A ferramenta SpiderFoot é um recurso valioso para pentesters durante a fase de Reconnaissance, oferecendo uma ampla gama de informações relevantes sobre o alvo. Ela suporta a integração com diversas fontes, permitindo a inclusão de chaves de APIs, o que expande significativamente a quantidade e a diversidade dos dados obtidos.

#### [From Nmap to CSV](https://www.secureideas.com/blog/from-nmap-to-csv)

Este script permite com que você transforme seu resultado do Nmap em uma planilha CSV, tornando assim mais fácil a visualização e organização.

Para utilização basta:

1. Rodar um scan com o Nmap e transformar o resultado em um arquivo "_.nmap_" (pode ser usado o ">" no Linux);
2. Em seguida rodamos o script da seguinte maneira: **nmap\_to\_csv.sh (arquivo.nmap) (arquivo\_de\_saida.csv)**;

Desta maneira conseguimos gerar o scan do Nmap em um arquivo CSV.

#### [Burp Variables](https://bishopfox.com/blog/burp-variables-burp-suite-extension)

Uma extensão do Burp Suite que permite a definição e reutilização de variáveis, como tokens de sessão e identificadores mutáveis, em requisições HTTP durantes os testes realizados. Ela automatiza a atualização dessas variáveis conforme seus valores mudam, economizando tempo e reduzindo erros manuais comuns ao manipular os dados em múltiplas requisições.

#### [MailSniper](https://github.com/dafthack/MailSniper)

É uma ferramenta utilizada para pesquisas de termos específicos como senhas, informações sobre arquitetura, e outras informações, através de um ambiente Microsoft Exchange.

A ferramenta também conta com módulos de password spray, enumeração de usuários  e domínios.

#### [MFASweep](https://github.com/dafthack/MFASweep)

Uma ferramenta desenvolvida com o intuito de verificar se o MFA está habilitado em múltiplos serviços da Microsoft.

#### [GraphRunner](https://github.com/dafthack/GraphRunner?tab=readme-ov-file)

Um conjunto de ferramentas utilizadas para pós-exploração, que realiza reconhecimento, persistência e busca de dados de uma conta Microsoft Entra ID (AD Azure) através da API Microsoft Graph.

