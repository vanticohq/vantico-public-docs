---
description: >-
  O serviço da web é o serviço mais comum e extenso e existem vários tipos
  diferentes de vulnerabilidades.
---

# Checklist

**Porta Padrão:** 80 (HTTP), 443 (HTTPS)

<pre><code><strong>PORT     STATE    SERVICE
</strong>80/tcp   open     http
443/tcp  open     ssl/https
</code></pre>

```
nc -v (domínio.com) 80 #GET / HTTP/1.0
openssl s_client -connect (domínio.com):443 #GET / HTTP/1.0
```



**Sumário de Metodologia**

> Nesta metodologia vamos supor que você vai atacar um domínio (ou subdomínio) e só isso. Portanto, você deve aplicar esta metodologia a cada domínio, subdomínio ou IP descoberto com servidor web indeterminado dentro do escopo.

* [ ] Comece identificando as tecnologias usadas no web server.&#x20;
  * [ ] Alguma vulnerabilidade conhecida da versão da tecnologia?
  * [ ] Usando alguma tecnologia conhecida? Algum truque útil para extrair mais informações?
  * [ ] Rodando algum scanner especializado (como wpscan)?
* [ ] Inicie scanners gerais. Você nunca sabe se eles vão encontrar algo ou se vão encontrar alguma informação interessante.
* [ ] Comece com as checagens iniciais: robots, sitemap, erro 404 e Scan SSL/TLS (se for HTTPS)
* [ ] Comece a rastrear a página da web: é hora de encontrar todos os arquivos, pastas e parâmetros possíveis que estão sendo usados. Além disso, verifique se há descobertas especiais.
  * [ ] Observe que sempre que um novo diretório for descoberto durante força bruta ou spidering, ele deverá ser indexado.
* [ ] Força bruta no diretório: tente aplicar força bruta em todas as pastas descobertas em busca de novos arquivos e diretórios.
* [ ] Verificação de backups: teste se você consegue encontrar backups de arquivos descobertos anexando extensões de backup comuns.
* [ ] Parâmetros de Força Bruta: Tente encontrar por parâmetros escondidos
* [ ] Depois de identificar todos os endpoints possíveis que aceitam a entrada do usuário, verifique todos os tipos de vulnerabilidades relacionadas a eles.



**Fase de Reconhecimento**

* Grande: Uma empresa com múltiplos domínios
* Média: Um único domínio
* Pequena: Um único website



**Escopo Grande**

* [ ] Busque ASN para encontrar até onde vai o IP (amass, anslookup, metabigor, bgp)
* [ ] Analise as últimas aquisições
* [ ] Consiga as relações dos registrantes (viewdns)
* [ ] Vá para o escopo médio para cada domínio



**Escopo Médio**

* [ ] Enumere os subdomínios (amass ou subfinder)
* [ ] Força Bruta nos subdomínios (puredns com wordlist)
* [ ] Identifique subdomínios ativos (httpx)
* [ ] Aquisição de subdomínios (nuclei-takeovers)
* [ ] Procure por ativos na nuvem (cloudenum)
* [ ] Pesquisa no Shodan
* [ ] Transfer Zone
* [ ] Pegar capturas de tela (gowitness, webscreenshot, aquatone)



**Escopo Pequeno**

* [ ] Identifique o servidor web, tecnologias e banco de dados (httpx)
* [ ] Tente localizar /robots.txt, /crossdomain.xml, /clientacesspolicy.xml, /sitemap.xml e /.well-know/
* [ ] Revise os comentários no Código Fonte (Ferramentas Burp)
* [ ] Enumeração do Diretório
* [ ] Web Fuzzing (ffuf e wordlist)
* [ ] Encontre IDs vazados, emails (pwndb)
* [ ] Identifique WAF (whatwaf, wafw00f)
* [ ] Google Dorking
* [ ] GitHub Dorking
* [ ] Busque URLs (gau, waybackurls, gospider)
* [ ] Busque por potenciais vulnerabilidades URLs (gf-patterns)
* [ ] Buscador automático de XSS (dalfox)
* [ ] Encontre o painel login e admin
* [ ] Hijack em links quebrados (blc)
* [ ] Consiga todos os arquivos JS (subjs, JSA, xnLinkFinder, getjswords)
* [ ] Rode scanner automáticos (nuclei)
* [ ] Teste CORS (CORScanner, corsy)



**Preparação**

* [ ] Estude a estrutura do site
* [ ] Faça uma lista de todos os possíveis testes
* [ ] Entenda sobre o negócio e o que seus clientes precisam
* [ ] Consiga uma lista com todos os ativos (all\_subdomains.txt, live\_subdomains.txt, waybackurls.txt, hidden\_directories.txt, nmap\_results.txt, GitHub\_search.txt, altdns\_subdomain.txt, vulnerable\_links.txt, js\_files.txt)



Enumerando as Aplicações do Web Server

* [ ] Enumerando com o NMAP
* [ ] Enumerando com o Netcat
* [ ] Execute uma consulta DNS
* [ ] Execute uma consulta DNS reversa



Revise o conteúdo da Web

* [ ] Inspecione a a fonte da página para informações sensíveis
* [ ] Tente encontrar códigos sensíveis de Javascript
* [ ] Tente encontrar alguma chave
* [ ] Tenha certeza que o autocompletar está desabilitado



Estrutura de aplicativo Web de impressão digital

* [ ] Use a extensão Wappalyzer do navegador
* [ ] Use Whatweb
* [ ] Veja as extensões URL
* [ ] Veja o código fonte HTML
* [ ] Veja os parâmetros do cookie
* [ ] Veja os cabeçalhos HTTP



Mapeie a Infraestrutura da Aplicação

* [ ] Mapeie toda a estrutura do site
* [ ] Segregação em infraestruturas compartilhadas
* [ ] Segregação entre aplicativos hospedados em ASP
* [ ] Vulnerabilidades do servidor web
* [ ] Métodos HTTP perigosos
* [ ] Funcionalidade de proxy
* [ ] Configuração incorreta de hospedagem virtual (VHostScan)
* [ ] Verifique os IPs internos na solicitação
* [ ] Verifique se há IPs externos e resolva-os
* [ ] Teste o armazenamento em nuvem
* [ ] Verifique a existência de canais alternativos (www.web.com vs m.web.com)



Enumeração da Infraestrutura e Interface Admin

* [ ] Tente encontrar a Interface da Infraestrutura
* [ ] Tente encontrar a Interface do Admin
* [ ] Identifique as funcionalidades escondidas do Admin



Mapeando Paths de Execução

* [ ] Use Burp Suite
* [ ] Use Dirsearch
* [ ] Use Gobuster



Identificar Pontos de Entrada na Aplicação

* [ ] Identificar quais métodos são usados
* [ ] Identificar onde estes métodos são usados
* [ ] Identificar o ponto de Injeção



**Rede**

* [ ] Verifique se pacotes ICMP estão permitidos
* [ ] Verifique as políticas DMARC/SPF (spoofcheck)
* [ ] Abra portas com o Shodan
* [ ] Port Scan em todas as portas
* [ ] Verifique as portas UDP (nmap)
* [ ] Teste SSL (testssl)
* [ ] Se possuir credenciais, tente pulverização de senhas em todos os serviços descobertos



**Teste a Configuração da Aplicação**

* [ ] Tenha certeza de que apenas os módulos requiridos são utilizados
* [ ] Tenha certeza de que módulos não requiridos estão desabilitados
* [ ] Tenha certeza de que o servidor suporta um DOS
* [ ] Verifique como a aplicação está lidando com os erros 4xx e 5xx
* [ ] Verifique os privilégios requiridos para funcionar
* [ ] Observe os logs para verificar informações sensíveis



**Teste o manuseio das Extensões de Arquivos**

* [ ] Tenha certeza de que o servidor não vai retornar extensões sensíveis
* [ ] Tenha certeza de que o servidor não aceita extensões maliciosas
* [ ] Teste as vulnerabilidades de uploads de arquivos



**Revise o Backup e Arquivos Não Referenciados**

* [ ] Tenha certeza de que arquivos não referenciados não contém informações sensíveis
* [ ] Tenha certeza das nomeações dos antigos e novos arquivos de backup
* [ ] Verifique a funcionalidade de páginas não referenciadas



**Teste as Permissões dos Arquivos**

* [ ] Tenha certeza das permissões dos arquivos sensíveis
* [ ] Realize um teste para enumeração de diretórios



**Teste a Aquisição de Subdomínios**

* [ ] Teste o DNS, A, as gravações do CNAME para aquisição de subdomínio
* [ ] Teste as gravações NS para aquisição de subdomínio
* [ ] Teste a resposta 404 para aquisição de subdomínio



**Teste o Armazenamento em Nuvem**

* [ ] Verifique por informações sensíveis nos paths da AWS
* [ ] Verifique por informações sensíveis nos paths do Google Cloud
* [ ] Verifique por informações sensíveis nos paths do Azure



**Verifique se você pode enviar arquivos (PUT, WebDav)**

Se você encontrar que WebDav está habilitado mas você não tem as permissões necessárias para enviar arquivos na pasta do root, tente:

* [ ] Força Bruta nas credenciais
* [ ] Enviar arquivos via WebDav para o restante das pastas encontradas dentro da página da web. Você pode ter permissões para fazer upload de arquivos em outras pastas.



**Teste páginas não Criptografadas**

* [ ] Verifique a página HTTP de login&#x20;
* [ ] Verifique a página HTTP de registro ou logar&#x20;
* [ ] Verifique a página HTTP Esqueci minha Senha
* [ ] Verifique a página HTTP Trocar minha Senha
* [ ] Verifique por recursos em HTTP depois de logar
* [ ] Teste forçar pesquisas em páginas HTTPS



**Teste por Credenciais Padrão**

* [ ] Teste com as credenciais padrão
* [ ] Teste o nome da organização como credencial
* [ ] Teste a manipulação de respostas
* [ ] Teste pelo nome de usuário padrão e uma senha em branco
* [ ] Procure no código fonte da página por credenciais



**Teste por mecanismos de bloqueios fracos**

* [ ] Tenha certeza de que a conta foi bloqueada depois de 3-5 tentativas
* [ ] Tenha certeza que o sistema aceite apenas CAPTCHA válido
* [ ] Tenha certeza que o sistema rejeite CAPTCHA inválido
* [ ] Tenha certeza de que o código do CAPTCHA é regerado após ser recarregado
* [ ] Tenha certeza de que o código CAPTCHA recarrega após colocar o código errado
* [ ] Tenha certeza de que há uma opção de recuperação para contas bloqueadas



**Teste para passar o sistema de autenticação**

* [ ] Teste uma pesquisa forçada diretamente do dashboard interno sem login
* [ ] Tente adivinhar o ID da sessão
* [ ] Tente adulterar parâmetros de autenticação
* [ ] Tente por Injeção SQL na página de login
* [ ] Tente ganhar acesso com a ajuda do ID da sessão
* [ ] Tente múltiplos logins permitidos ou não?



**Teste por vulnerabilidades em Lembrar a Senha**

* [ ] Tenha certeza de que as senhas armazenadas estão criptografadas
* [ ] Tenha certeza de que as senhas armazenadas estão no lado do servidor



**Teste por fraquezas no cache do navegador**

* [ ] Tenha certeza que o controle do cache está configurado em páginas sensíveis
* [ ] Tenha certeza de que não há dados sensíveis armazenados no cache do navegador



**Teste por Políticas de Senhas Fracas**

* [ ] Tenha certeza de que a política de senhas é forte
* [ ] Verifique se a senha pode ser reutilizada
* [ ] Verifique uma wordlist de senhas (cewl e burp-goldenNuggets)
* [ ] Verifique se o usuário é permitido utilizar seu nome de usuário como sua senha
* [ ] Verifique se há o uso de senhas fracas comuns
* [ ] Verifique se a quantidade mínimas de caracteres está configurada
* [ ] Verifique se a quantidade máxima de caracteres está configurada



**Verifique por Questão de Segurança Fracas**

* [ ] Verifique a complexidade das questões
* [ ] Verifique por força bruta



**Teste a função de Resetar a Senha é Fraca**

* [ ] Verifique qual informação é necessária para resetar a senha
* [ ] Verifique a função de resetar a senha com HTTP
* [ ] Teste a randomização dos tokens de resetar a senha
* [ ] Teste a unicidade dos tokens de resetar a senha
* [ ] Verifique a taxa limite dos tokens de resetar a senha
* [ ] Tenha certeza de que os tokens expiram após serem usados
* [ ] Tenha certeza de que os tokens expiram depois de um longo tempo sem serem usados



**Teste a função de Trocar a Senha é Fraca**

* [ ] Verifique se uma senha antiga é requisitada para trocar a senha
* [ ] Verifique pela unicidade de uma senha esquecida
* [ ] Verifique pela troca de senha em branco
* [ ] Verifique a função de trocar a senha com HTTP
* [ ] Tenha certeza de que a antiga senha não irá aparecer no painel
* [ ] Tenha certeza de que as outras sessões vão ser destruídas depois de trocar a senha



**Teste por uma Autenticação Fraca em um Canal Alternativo**

* [ ] Teste por autenticação em navegadores de computador
* [ ] Teste por autenticação em navegadores de celulares
* [ ] Teste por autenticação em diferentes países
* [ ] Teste por autenticação em diferentes línguas
* [ ] Teste por autenticação por aplicações de computador
* [ ] Teste por autenticação por aplicação de celulares



**Teste o Processo de Registro dos Usuários**

* [ ] Tenha certeza de que o mesmo usuário não pode se registrar novamente
* [ ] Tenha certeza de que os registros são verificados
* [ ] Tenha certeza de que emails descartáveis são rejeitados
* [ ] Verifique qual prova é requirida para um registro com sucesso
* [ ] Verifique o Registro Duplo
* [ ] A unicidade do nome dos usuários
* [ ] Adicionar apenas espaços na senha
* [ ] A taxa limite de tempo de registro
* [ ] XSS no nome ou email



**Teste a Inclusão de Arquivos no Diretório**

* [ ] Identifique o ponto de injeção na URL
* [ ] Teste pela inclusão de arquivo local
* [ ] Teste pela inclusão de arquivo remoto



**Teste Traversal com Codificação**

* [ ] Teste Traversal com codificação Base64
* [ ] Teste Traversal com codificação URL
* [ ] Teste Traversal com codificação ASCII
* [ ] Teste Traversal com codificação HTML
* [ ] Teste Traversal com codificação Hex
* [ ] Teste Traversal com codificação Binário
* [ ] Teste Traversal com codificação Octal
* [ ] Teste Traversal com codificação Gzip



**Teste Outras formas de Codificação**

* [ ] Teste Traversal com Codificação Dupla
* [ ] Teste Traversal com todos os caracteres de codificação
* [ ] Teste Traversal com codificação de apenas caracteres especiais



**Teste por Escalação de Privilégios**

* [ ] Identifique o ponto de Injeção
* [ ] Teste dar bypass nas medidas de segurança
* [ ] Teste com pesquisa forçada
* [ ] Teste por IDOR
* [ ] Teste para adulteração de parâmetros para usuário com alto privilégio



**Teste para referência direta de objeto inseguro**

* [ ] Teste para alterar o parâmetro ID
* [ ] Teste para adicionar parâmetros nos endpoints
* [ ] Teste para poluição de parâmetros HTTP
* [ ] Teste adicionando uma extensão no final
* [ ] Teste com versões de API desatualizadas
* [ ] Teste envolvendo o ID com uma matriz
* [ ] Teste agrupando o ID com um objeto JSON
* [ ] Teste para poluição de parâmetros JSON
* [ ] Teste alterando o caso
* [ ] Teste mudando palavras
* [ ] Teste alterando métodos



**Teste para gerenciamento de sessão**

* [ ] Garanta que todas as diretivas Set-Cookie sejam seguras
* [ ] Garanta que nenhuma operação de cookie ocorra em um canal não criptografado
* [ ] Garanta que o cookie não possa ser forçado em um canal não criptografado
* [ ] Certifique-se de que o sinalizador HTTPOnly esteja ativado
* [ ] Verifique se algum cookie é persistente
* [ ] Verifique os cookies de sessão e a data/hora de expiração dos cookies
* [ ] Verifique a fixação da sessão
* [ ] Verifique se há login simultâneo
* [ ] Verifique a sessão após o logout
* [ ] Verifique a sessão após fechar o navegador
* [ ] Tente decodificar cookies (Base64, Hex, URL, etc)



**Teste para Atributos de Cookies**

* [ ] Certifique-se de que o cookie deve ser definido com o atributo seguro
* [ ] Certifique-se de que o cookie deve ser definido com o atributo path
* [ ] Certifique-se de que o cookie deve ter o sinalizador HTTPOnly



**Teste para fixação de sessão**

* [ ] Garanta que novos cookies tenham sido emitidos após uma autenticação bem-sucedida
* [ ] Teste a manipulação dos cookies



**Teste para variáveis de sessão expostas**

* [ ] Teste de criptografia
* [ ] Teste as vulnerabilidades GET e POST
* [ ] Teste se a solicitação GET incorpora o ID de sessão usado
* [ ] Teste trocando o método POST pelo método GET



**Teste para ataque de atualização posterior**

* [ ] Teste após alteração de senha
* [ ] Teste depois de sair da conta



**Teste para falsificação de solicitação entre sites**

* [ ] Verifique se o token é validado no lado do servidor ou não
* [ ] Verifique se o token está validado para comprimento total ou parcial
* [ ] Verifique comparando os tokens CSRF para várias contas fictícias
* [ ] Verifique CSRF trocando POST pelo método GET



**Teste a funcionalidade de logout**

* [ ] Verifique a função de logout em diferentes páginas
* [ ] Verifique a visibilidade do botão de logout
* [ ] Certifique-se de que após o logout a sessão foi encerrada
* [ ] Certifique-se de que, após o logout, não consigamos acessar o painel pressionando o botão Voltar
* [ ] Certifique-se de que o tempo limite da sessão adequado foi definido



**Teste o tempo limite da sessão**

* [ ] Certifique-se de que existe um tempo limite de sessão
* [ ] Certifique-se de que após o tempo limite todos os tokens sejam destruídos



**Teste para sequestro de sessão**

* [ ] Teste o sequestro de sessão no alvo que não tem HSTS ativado
* [ ] Teste por login com ajuda de cookies capturados



**Teste para Refleted Cross Site Scripting**

* [ ] Certifique-se de que esses caracteres sejam filtrados <> "&"
* [ ] Teste com uma sequência de escape de caracteres
* [ ] Teste substituindo < e > por entidades HTML < e >
* [ ] Teste payload com letras maiúsculas e minúsculas
* [ ] Teste para quebrar o regex do firewall pela nova linha /r/n
* [ ] Teste com codificação dupla
* [ ] Teste com filtros recursivos
* [ ] Teste a injeção de tags âncora sem espaços em branco
* [ ] Teste substituindo espaços em branco por marcadores
* [ ] Teste alterando os métodos HTTP



**Teste para Stored Cross Site Scripting**

* [ ] Identifique os parâmetros de entrada armazenados que refletirão no lado do cliente
* [ ] Procure parâmetros de entrada na página de perfil
* [ ] Procure os parâmetros de entrada na página do carrinho de compras
* [ ] Procure os parâmetros de entrada na página de upload do arquivo
* [ ] Procure os parâmetros de entrada na página de configurações
* [ ] Procure parâmetros de entrada no fórum, página de comentários
* [ ] Teste o upload de um arquivo com payload XSS como nome de arquivo
* [ ] Teste com tags HTML



**Teste de poluição de parâmetros HTTP**

* [ ] Identifique o servidor back-end e o método de análise usado
* [ ] Tente acessar o ponto de injeção
* [ ] Tente ignorar os filtros de entrada usando a poluição de parâmetros HTTP



**Teste para injeção SQL**

* [ ] Teste SQL Injection em formulários de autenticação
* [ ] Teste a injeção de SQL na barra de pesquisa
* [ ] Teste a injeção de SQL em características editáveis
* [ ] Tente encontrar palavras-chave SQL ou detecções de pontos de entrada
* [ ] Tente injetar consultas SQL
* [ ] Injeção SQL com ' and '--+-
* [ ] Use ferramentas como SQLmap ou Hackbar
* [ ] Use o Google Dorks para encontrar as palavras-chave SQL
* [ ] Experimente injeção SQL baseada em GET, POST, COOKIE, HEADER
* [ ] Experimente SQL Injection com bytes nulos antes da consulta SQL
* [ ] Experimente SQL Injection com codificação de URL
* [ ] Experimente SQL Injection com letras maiúsculas e minúsculas
* [ ] Experimente SQL Injection com scripts SQL Tamper
* [ ] Experimente SQL Injection com payloads de atraso de tempo SQL
* [ ] Experimente SQL Injection com atrasos condicionais de SQL
* [ ] Experimente SQL Injection com SQL baseado em Boolean
* [ ] Experimente SQL Injection com SQL baseado em tempo



**Teste a Injeção XML**

* [ ] Verifique se o aplicativo está usando XML para processamento
* [ ] Identifique o ponto de injeção XML por metacaractere XML
* [ ] Construa payload XSS sobre XML



**Teste para inclusão do lado do servidor**

* [ ] Use Google Dorks para encontrar SSI
* [ ] Construa RCE em cima do SSI
* [ ] Construa outras injeções além do SSI
* [ ] Teste a injeção de SSI em páginas de login, campos de cabeçalho, referenciador, etc.



**Teste por Injeção IMAP SMTP**

* [ ] Identificar o ponto de injeção IMAP SMTP
* [ ] Entenda o fluxo de dados
* [ ] Entenda a estrutura de implantação do sistema
* [ ] Avalie o impacto da injeção



**Teste para inclusão de arquivo local**

* [ ] Procure palavras-chave LFI
* [ ] Tente mudar o caminho local
* [ ] Use a lista de payloads LFI
* [ ] Teste o LFI adicionando um byte nulo no final



**Teste para inclusão remota de arquivos**

* [ ] Procure palavras-chave RFI
* [ ] Tente mudar o caminho remoto
* [ ] Use a lista de payloads RFI



**Teste para injeção de comando**

* [ ] Identifique os pontos de injeção
* [ ] Procure palavras-chave de injeção de comando
* [ ] Teste a injeção de comando usando diferentes delimitadores
* [ ] Testar injeção de comando com lista de payloads
* [ ] Teste a injeção de comando com diferentes comandos do sistema operacional



**Teste para injeção de string de formato**

* [ ] Identifique os pontos de injeção
* [ ] Use parâmetros de formato diferentes como payloads
* [ ] Avalie o impacto da injeção



**Teste para injeção de cabeçalho de host**

* [ ] Teste o HHI alterando o parâmetro real do Host
* [ ] Fuzz todos os parâmetros de solicitação (se tiver usuário, adicione cabeçalhos ao fuzzer)
* [ ] Teste o HHI adicionando o parâmetro X-Forwarded Host
* [ ] Teste o HHI trocando o parâmetro Host real e Host encaminhado por X
* [ ] Teste o HHI adicionando dois parâmetros de host
* [ ] Teste o HHI adicionando os valores alvo na frente dos valores originais
* [ ] Teste o HHI adicionando o alvo com uma barra após os valores originais
* [ ] Teste para HHI com outras injeções no parâmetro Host
* [ ] Teste para HHI por envenenamento por redefinição de senha



**Teste para falsificação de solicitação do servidor**

* [ ] Procure palavras-chave SSRF
* [ ] Pesquise palavras-chave SSRF apenas no cabeçalho e no corpo da solicitação
* [ ] Identifique os pontos de injeção
* [ ] Teste se os pontos de injeção são exploráveis
* [ ] Avalie o impacto da injeção



**Teste para injeção de modelo no lado do servidor**

* [ ] Identifique os pontos de vulnerabilidade de injeção de modelo
* [ ] Identifique o mecanismo de modelagem
* [ ] Use o tplmap para explorar



**Teste para tratamento de erros inadequado**

* [ ] Identifique a saída do erro
* [ ] Analise as diferentes saídas retornadas
* [ ] Procure falhas comuns no tratamento de erros
* [ ] Teste o tratamento de erros modificando o parâmetro URL
* [ ] Teste o tratamento de erros fazendo upload de formatos de arquivo não reconhecidos
* [ ] Teste o tratamento de erros inserindo entradas não reconhecidas
* [ ] Teste o tratamento de erros cometendo todos os erros possíveis



**Teste para segurança fraca da camada de transporte**

* [ ] Teste a fraqueza do DROWN no protocolo SSLv2
* [ ] Teste a fraqueza do POODLE no protocolo SSLv3
* [ ] Teste a fraqueza do BEAST no protocolo TLSv1.0
* [ ] Teste a fraqueza FREAK em conjuntos de cifras de exportação
* [ ] Teste para cifras nulas
* [ ] Teste para NOMORE fraqueza no RC4
* [ ] Teste a fraqueza do LUCKY 13 nas cifras do modo CBC
* [ ] Teste a fraqueza do CRIME na compactação TLS
* [ ] Teste para LOGJAM em chaves DHE
* [ ] Certifique-se de que os certificados digitais tenham pelo menos 2.048 bits de comprimento de chave
* [ ] Certifique-se de que os certificados digitais tenham pelo menos o algoritmo de assinatura SHA-256
* [ ] Certifique-se de que os certificados digitais não devem usar MDF e SHA-1
* [ ] Garanta a validade do certificado digital
* [ ] Garanta os requisitos mínimos de comprimento de chave
* [ ] Procure por conjuntos de criptografia fracos



**Lógica do Negócio**

* [ ] Identifique a lógica de como o aplicativo funciona
* [ ] Identifique a funcionalidade de todos os botões
* [ ] Teste alterando os valores numéricos para valores altos ou negativos
* [ ] Teste alterando a quantidade
* [ ] Teste o upload de arquivos maliciosos enviando arquivos maliciosos
* [ ] Teste o upload de arquivos maliciosos colocando seu endereço IP no nome do arquivo
* [ ] Teste o upload de arquivos maliciosos por nome de arquivo codificado
* [ ] Teste o upload de arquivo malicioso por payload XSS, RCE, LFI, SQL ou outros no nome do arquivo
* [ ] Teste o upload de arquivos maliciosos enviando arquivos grandes (leva ao DOS)
* [ ] Identifique a superfície de ataque lógico
* [ ] Teste a transmissão de dados através do cliente
* [ ] Teste a dependência da validação de entrada do lado do cliente
* [ ] Componentes de cliente espesso (Java, ActiveX, Flash)
* [ ] Processos de vários estágios para falhas lógicas
* [ ] Tratamento de entrada incompleta
* [ ] Limites de confiança
* [ ] Lógica de transação
* [ ] Implemente CAPTCHA em formulários de e-mail para evitar inundações
* [ ] Adulterar ID do produto, preço ou valor da quantidade em qualquer ação (adicionar, modificar, excluir, colocar, pagar...)
* [ ] Adulteração de presentes ou códigos de desconto
* [ ] Reutilize códigos de presente
* [ ] Tente a poluição do parâmetro para usar o código de presente duas vezes na mesma solicitação
* [ ] Experimente XSS armazenado em campos não limitados, como endereço
* [ ] Verifique no formulário de pagamento se o CVV e o número do cartão estão em texto claro ou mascarados
* [ ] Verifique se é processado pelo próprio aplicativo ou enviado para terceiros
* [ ] IDOR de outros usuários detalha bilhete/carrinho/remessa
* [ ] Verifique o número do cartão de crédito de teste permitido, como 4111 1111 1111 1111 (amostra1 amostra2)
* [ ] Verifique a criação de PRINT ou PDF para IDOR
* [ ] Verifique o botão de cancelamento de inscrição com enumeração de usuários
* [ ] Poluição de parâmetros em links de compartilhamento de mídia social
* [ ] Altere as solicitações confidenciais do POST para GET



**Teste para scripts entre sites baseados em DOM**

* [ ] Tente identificar coletores DOM
* [ ] Crie payloads para esse tipo de coletor DOM



**Teste para redirecionamento de URL**

* [ ] Procure parâmetros de redirecionamento de URL
* [ ] Teste o redirecionamento de URL em parâmetros de domínio
* [ ] Teste o redirecionamento de URL usando uma lista de payloads
* [ ] Teste o redirecionamento de URL usando uma palavra da lista de permissões no final
* [ ] Teste o redirecionamento de URL criando um novo subdomínio com o mesmo destino
* [ ] Teste para redirecionamento de URL por XSS
* [ ] Teste o redirecionamento de URL por falha de URL do perfil



**Teste para compartilhamento de recursos entre origens**

* [ ] Procure por “Access-Control-Allow-Origin” na resposta
* [ ] Use o código de exploração HTML CORS para exploração adicional



**Teste para clickjacking**

* [ ] Certifique-se de que os cabeçalhos “X-Frame-Options” estejam ativados
* [ ] Explorar com código HTML iframe para POC



**Teste para limitação sem taxa**

* [ ] Certifique-se de que a limitação de taxa esteja habilitada
* [ ] Tente contornar a limitação de taxa alterando a caixa dos endpoints
* [ ] Tente contornar a limitação de taxa adicionando / no final do URL
* [ ] Tente contornar a limitação de taxa adicionando cabeçalhos HTTP
* [ ] Tente contornar a limitação de taxa adicionando cabeçalhos HTTP duas vezes
* [ ] Tente contornar a limitação de taxa adicionando cabeçalhos Origin
* [ ] Tente contornar a limitação de taxa por rotação de IP
* [ ] Tente ignorar a limitação de taxa usando bytes nulos no final
* [ ] Tente contornar a limitação de taxa usando condições de corrida



**Teste para geodados EXIF**

* [ ] Certifique-se de que o site esteja distribuindo os geodados
* [ ] Teste com verificador EXIF



**Teste de sequestro de link quebrado**

* [ ] Certifique-se de que não haja links quebrados
* [ ] Teste links quebrados usando a ferramenta blc



**Teste por SPF**

* [ ] Certifique-se de que o site tenha registro SPF
* [ ] Teste o SPF pelo comando nslookup



**Teste para 2FA fraco**

* [ ] Tente contornar o 2FA usando um gerenciamento de sessão inadequado
* [ ] Tente ignorar o 2FA por meio do mecanismo OAuth
* [ ] Tente contornar o 2FA por meio de força bruta
* [ ] Tente contornar o 2FA através da manipulação de resposta
* [ ] Tente ignorar o 2FA usando links de ativação para fazer login
* [ ] Tente contornar 2FA usando manipulação de código de status
* [ ] Tente contornar o 2FA alterando o e-mail ou senha
* [ ] Tente ignorar 2FA usando uma entrada nula ou vazia
* [ ] Tente ignorar o 2FA alterando o boolean para falso
* [ ] Tente ignorar o 2FA removendo o parâmetro 2FA na solicitação



**Teste para implementação de OTP fraca**

* [ ] Tente ignorar o OTP inserindo o OTP antigo
* [ ] Tente contornar o OTP por força bruta
* [ ] Tente ignorar o OTP usando uma entrada nula ou vazia
* [ ] Tente contornar o OTP manipulando a resposta
* [ ] Tente ignorar o OTP manipulando o código de status



**CAPTCHA**

* [ ] Envie o valor antigo do captcha.
* [ ] Envie o valor captcha antigo com o ID de sessão antigo.
* [ ] Solicite o caminho absoluto do captcha como www.url.com/captcha/1.png
* [ ] Remova o captcha com qualquer adblocker e solicite novamente
* [ ] Ignorar com ferramenta OCR
* [ ] Mudar de POST para GET
* [ ] Remover parâmetro captcha
* [ ] Converter solicitação JSON em normal
* [ ] Experimente injeções de cabeçalho



**Cabeçalhos de segurança**

* [ ] X-XSS-Protection
* [ ] Strict-Transport-Security
* [ ] Content-Security-Policy
* [ ] Public-Key-Pins
* [ ] X-Frame-Options
* [ ] X-Content-Type-Options
* [ ] Referer-Policy
* [ ] Cache-Control
* [ ] Expires



**Forçando Erros**

Os servidores da Web podem se comportar de maneira inesperada quando dados estranhos são enviados a eles. Isso pode abrir vulnerabilidades ou divulgar informações confidenciais.

* [ ] Acesse as páginas falsas como qualquer\_página.php (aspx, html, etc)
* [ ] Adicione "\[]", "]]", e "\[\[" nos valores dos cookies e valores dos parâmetros para criar erros
* [ ] Gere erros colocando "/\~randomthing/%s" no fim da URL
* [ ] Adicione diversos parâmetros como GET e POST usando diferentes valores
* [ ] Use o Burp Intruder "Fuzzing Full" Lista em entrada para gerar códigos de erros
* [ ] Tente diferentes verbos HTTP como PATCH, DEBUG ou algo como FAKE



**Vulnerabilidades SSL/TLS**

* [ ] Se a aplicação não está forçando o usuário HTTPS em alguma parte, então é vulnerável para o MitM
* [ ] Se a aplicação está enviando dados sensíveis (senhas) usando HTTP. Então isto é uma vulnerabilidade alta

Use testssl.sh para verificar as vulnerabilidades e use a2sv para verificar novamente as vulnerabilidades

```
./testssl.sh [--htmlfile] 10.10.10.10:443
#Use o --htmlfile para salvar a saída dentro de um arquivo html

#Você pode também usar outras ferramentas, o testssl.sh neste momente é a melhor
sslscan <host:porta>
sslyze --regular <ip:porta>
```

Informações sobre vulnerabilidades SSL/TSL:

{% embed url="https://www.gracefulsecurity.com/tls-ssl-vulnerabilities/" %}

{% embed url="https://www.acunetix.com/blog/articles/tls-vulnerabilities-attacks-final-part/" %}

**Spidering**

Envie um tipo de aranha dentro da teia. A meta do spider é encontrar o máximo de paths possíveis da aplicação testada. Portanto, web crawling e fontes externas devem ser usadas para encontrar o máximo de paths possíveis.

* [ ] gospider - Spider HTML, LinkFinder em arquivos JS e fontes externas (Archive.org, CommonCrawl.org, VirusTotal.com, AlienVault.com).
* [ ] hakrawler - Spider HML, com LinkFider para arquivos JS e Archive.org como fonte externa.
* [ ] dirhunt - HTML spider, também indica "arquivos suculentos".
* [ ] evine - Spider HTML CLI interativa. Ele também pesquisa no Archive.org
* [ ] meg - Esta ferramenta não é uma spider, mas pode ser útil. Você pode apenas indicar um arquivo com hosts e um arquivo com caminhos e meg irá buscar cada caminho em cada host e salvar a resposta.
* [ ] urlgrab - Spider HTML com recursos de renderização JS. Porém, parece que não tem manutenção, a versão pré-compilada é antiga e o código atual não compila
* [ ] gau - Spider HTML que usa provedores externos (wayback, otx, commoncrawl)
* [ ] ParamSpider - Este script encontrará URLs com parâmetro e os listará.
* [ ] galer - Spider HTML com recursos de renderização JS.
* [ ] LinkFinder - HTML spider, com recursos de embelezamento JS capazes de pesquisar novos caminhos em arquivos JS. Também pode valer a pena dar uma olhada no JSScanner, que é um wrapper do LinkFinder.
* [ ] goLinkFinder - Para extrair endpoints em arquivos de origem HTML e javascript incorporados. Útil para caçadores de bugs, red teamers, ninjas da infosec.
* [ ] dirhunt - HTML spider, também indica "arquivos suculentos".
* [ ] JSParser - Um script python 2.7 usando Tornado e JSBeautifier para analisar URLs relativos de arquivos JavaScript. Útil para descobrir facilmente solicitações AJAX. Parece sem manutenção.
* [ ] relative-url-extractor - Dado um arquivo (HTML), ele extrairá URLs dele usando uma expressão regular bacana para encontrar e extrair os URLs relativos de arquivos feios (minificar).
* [ ] JSFScan - Reúna informações interessantes de arquivos JS usando diversas ferramentas.
* [ ] subjs - Encontre arquivos JS.
* [ ] page-fetch - Carregue uma página em um navegador sem cabeça e imprima todos os URLs carregados para carregar a página.
* [ ] Feroxbuster - Ferramenta de descoberta de conteúdo misturando diversas opções das ferramentas anteriores
* [ ] JavaScript Parsing - Uma extensão Burp para encontrar caminhos e parâmetros em arquivos JS.
* [ ] Sourcemapper - Uma ferramenta que fornece o URL .js.map fornecerá o código JS beatificado
* [ ] xnLinkFinder - Esta é uma ferramenta usada para descobrir endpoints para um determinado alvo.
* [ ] waymore - Descubra links da máquina wayback (também baixando as respostas no wayback e procurando mais links
* [ ] HTTPLoot - Rastreie (até mesmo preenchendo formulários) e também encontre informações confidenciais usando expressões regulares específicas.
* [ ] SpiderSuite - Spider Suite é um crawler/Spider avançado de segurança da web com GUI multifuncional projetado para profissionais de segurança cibernética.
* [ ] jsluice - É um pacote Go e uma ferramenta de linha de comando para extrair URLs, caminhos, segredos e outros dados interessantes do código-fonte JavaScript.
* [ ] ParaForge - ParaForge é uma extensão simples do Burp Suite para extrair os parâmetros e endpoints da solicitação para criar uma lista de palavras personalizada para difusão e enumeração.
* [ ] katana - Ferramenta incrível para isso.



**Força Bruta nos Diretórios e Arquivos**

Inicie a força bruta a partir da pasta root e certifique-se de aplicar força bruta em todos os diretórios encontrados usando este método e em todos os diretórios descobertos pelo Spidering (você pode fazer essa força bruta recursivamente e anexando no início da lista de palavras usada os nomes dos diretórios encontrados).

Ferramentas:

* [ ] Dirb/ Dirbuster - Incluído no Kali, antigo (e lento), mas funcional. Permitir certificados assinados automaticamente e pesquisa recursiva. Muito lento em comparação com outras opções.
* [ ] Dirsearch - Não permite certificados assinados automaticamente, mas permite pesquisa recursiva.
* [ ] Gobuster - Permite certificados autoassinados, não possui pesquisa recursiva.
* [ ] Feroxbuster - Rápido, suporta pesquisa recursiva.
* [ ] wfuzz

```
wfuzz -w /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt 
https://domain.com/api/FUZZ
```

* [ ] ffuf

```
ffuf -c -w /usr/share/wordlists/dirb/big.txt -u http://10.10.10.10/FUZZ
```

* [ ] uro - Este não é um spider, mas uma ferramenta que, dada a lista de URLs encontrados, excluirá URLs "duplicados".
* [ ] Scavenger - Extensão Burp para criar uma lista de diretórios a partir do histórico de arrotos de diferentes páginas
* [ ] TrashCompactor - Remova URLs com funcionalidades duplicadas (com base em importações js)
* [ ] Chamaleon - Ele usa wapalyzer para detectar tecnologias usadas e selecionar as listas de palavras a serem usadas.



**O que Verificar em cada Arquivo Encontrado**

* [ ] Verificador de links quebrados: Encontre links quebrados dentro de HTMLs que podem estar sujeitos a aquisições
* [ ] Backups de arquivos: Depois de encontrar todos os arquivos, procure backups de todos os arquivos executáveis ​​(".php", ".aspx"...). Variações comuns para nomear um backup são: file.ext\~, #file.ext#, \~file.ext, file.ext.bak, file.ext.tmp, file.ext.old, file.bak, file.tmp e arquivo.old. Você também pode usar a ferramenta bfac ou backup-gen.
* [ ] Descubra novos parâmetros: você pode usar ferramentas como Arjun, parameth, x8 e Param Miner para descobrir parâmetros ocultos. Se puder, você pode tentar pesquisar parâmetros ocultos em cada arquivo executável da web.
* [ ] Comentários: Verifique os comentários de todos os arquivos, você pode encontrar credenciais ou funcionalidades ocultas.
* [ ] Chaves de API: Se você encontrar alguma chave de API, há um guia que indica como usar chaves de API de diferentes plataformas: keyhacks, zile, truffeHog, SecretFinder, RegHex, DumpsterDive, EarlyBird
* [ ] Buckets S3: Durante a pesquisa, verifique se algum subdomínio ou link está relacionado a algum bucket S3. Nesse caso, verifique as permissões do bucket.



**Descobertas Especiais**

* [ ] Ao realizar o spidering e a força bruta, você poderá encontrar coisas interessantes que precisa observar.

<!---->

* Arquivos Interessantes

<!---->

* [ ] Procure links para outros arquivos dentro dos arquivos CSS.
* [ ] Se você encontrar um arquivo .git, algumas informações poderão ser extraídas
* [ ] Se você encontrar um .env, informações como chaves de API, senhas de banco de dados e outras informações podem ser encontradas.
* [ ] Se você encontrar endpoints de API, também deverá testá-los. Estes não são arquivos, mas provavelmente serão "parecidos" com eles.
* [ ] Arquivos JS: Na seção de spidering foram mencionadas várias ferramentas que podem extrair o caminho dos arquivos JS. Além disso, seria interessante monitorar cada arquivo JS encontrado, pois em alguns locais, uma alteração pode indicar que uma potencial vulnerabilidade foi introduzida no código. Você poderia usar, por exemplo, JSMon.
* [ ] Você também pode monitorar os arquivos onde os formulários foram detectados, pois uma alteração no parâmetro ou o aparecimento de um novo formulário pode indicar uma potencial nova funcionalidade vulnerável.



**Monitore as páginas em busca de alterações**

* [ ] Você pode usar ferramentas como https://github.com/dgtlmoon/changedetection.io para monitorar páginas em busca de modificações que possam inserir vulnerabilidades.

