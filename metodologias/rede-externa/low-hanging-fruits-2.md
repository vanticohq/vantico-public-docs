# Low Hanging Fruits 2

O pentest irá passar pelos seguintes estágios:

* [Reconhecimento](low-hanging-fruits-2.md#reconhecimento)
* [Descoberta de serviços](low-hanging-fruits-2.md#descobertas-de-servicos)
* [Scans de vulnerabilidade](low-hanging-fruits-2.md#scans-de-vulnerablidade)
* [Avaliação Manual](low-hanging-fruits-2.md#avaliacao-manual)
* [Testes Adicionais](low-hanging-fruits-2.md#testes-adicionais)



### Reconhecimento

Nesta fase irá ser procurado por informações através de OSINT (Open Source Intelligence), ou seja, informações presentes dentro da internet de forma com que qualquer usuário pode conseguir. Itens que podem ser consultados nesta fase:

* URLs
* Informações de contato
* Informações de domínio
* Links para outros servidores da corporação
* Outras companias linkadas a seu site
* Informações de políticas de segurança
* Whois



#### Ferramentas

Durante esta fase foram usadas as seguintes ferramentas:

* Nmap
* DirBuster
* Shodan
* Censys

***



### Descobertas de serviços

Depois de buscar por todas as informações disponíveis, passa agora para uma fase mais objetiva no alvo, buscando testes como [Port Scans](low-hanging-fruits-2.md#port-scan) e [Investigações profundas](low-hanging-fruits-2.md#investigacoes-profundas).

#### Ferramentas

Durante esta fase foram usadas as seguintes ferramentas:

* Nmap
* Aquatone
* EyeWitness
* testssl.sh



### Port Scan

Os pentesters podem performar uma busca completa pelo range de IPs da empresa a fim de identificar serviços possivelmente vulneráveis funcionando, tais como:

* Firewall
* Web Server
* FTP



### Investigações profundas

Com base nos resultados da varredura inicial de portas, nossos pentesters trabalham para identificar:

* Os tipos de aplicativos em execução em máquinas expostas externamente
* As versões do software encontrado
* Os sistemas operacionais nos quais o software é executado

Em alguns casos, uma máquina exposta externamente pode apresentar serviços abertos sem funções específicas associadas. Os pentesters podem identificá-los e direcioná-los para testes.

***



### Scans de vulnerablidade

Os pentesters da Vantico, em seguida, identificam vulnerabilidades na parte da rede voltada para o público externo. O objetivo é penetrar nos endpoints externos para obter acesso à LAN interna e aos recursos da organização.

Se um possível invasor alcançar esse objetivo, a organização poderá enfrentar:

* Vazamento de informações sensíveis ou confidenciais da rede corporativa. A exfiltração de segredos comerciais ou dados de comunicação interna pode prejudicar a organização afetada. Entre as informações que podem ser vazadas estão:
  * Registros pessoais
  * Dados de pagamento
  * Outros registros financeiros
* Uso do gateway de e-mail ou do site como fonte de spam. Outros sites podem colocar o domínio da organização em listas de bloqueio, rejeitando automaticamente e-mails legítimos.
* Interrupções de serviço, chegando ao ponto de os recursos da organização ficarem indisponíveis, seja temporária ou permanentemente.
* Desfiguração (defacement) do site. Os invasores podem até mesmo substituir o site por uma versão própria, onde clientes atuais ou potenciais fazem login. A organização pode perder credibilidade ou até mesmo clientes em potencial.



#### Ferramentas

Durante esta fase foram usadas as seguintes ferramentas

* Metasploit
* Nessus
* Nmap
* Burp Suite Community/Professional
* Nikto



***



### Avaliação Manual

Durante a avaliação manual, os pentesters da Vantico analisam recursos específicos que foram identificados. Na maioria dos casos, eles se concentram em serviços visivelmente abertos:

* Servidores web
* Servidores FTP
* Servidores de e-mail
* Firewalls
* Roteadores
* Servidores DNS
* Outros serviços executados no intervalo de IPs externos, incluindo serviços do Office 365



#### Ferramentas

Durante esta fase foram usadas as seguintes ferramentas:

* Burp Suite Community/Professional
* Metasploit
* sqlmap
* Postman



***



### Testes Adicionais

Os pentesters da Vantico utilizam diversas ferramentas personalizadas e disponíveis publicamente ao longo de um pentest, como:

* Varredores de portas (port scanners)
* Scanners automáticos de vulnerabilidades
* Proxies HTTP
* Exploits
* Scripts personalizados
* Aplicativos de segurança











o1

















