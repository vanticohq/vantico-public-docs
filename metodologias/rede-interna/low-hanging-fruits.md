# Low Hanging Fruits

O pentest irá passar pelos seguintes estágios:

* [Descoberta de Serviços](low-hanging-fruits.md#descoberta-de-servicos)
* [Scans de vulnerabilidades](low-hanging-fruits.md#scans-de-vulnerabilidades)
* [Avaliação Manual](low-hanging-fruits.md#avaliacao-manual)



### Descoberta de Serviços

#### Portscan

Os pentesters realizam uma varredura completa de portas nos intervalos de rede interna fornecidos. Isso fornece um detalhamento minucioso das máquinas e dos serviços em execução dentro da rede corporativa, bem como as funções que exercem.

Por exemplo, os seguintes serviços requerem acesso à rede para funcionar:

* Servidores de arquivos
* Servidores de e-mail
* Servidores web
* Dispositivos de rede conectados (impressoras e telefones)
* Servidores FTP
* Servidores e clientes Active Directory (AD)

Todos esses serviços deixam assinaturas características que podem ser detectadas por uma varredura de portas.



#### Ferramentas

Durante esta fase foram usadas as seguintes ferramentas:

* Nmap
* Masscan



***



### Scans de vulnerabilidades

Os pentesters da Vantico realizam varreduras de vulnerabilidade para oferecer uma avaliação abrangente. Nesta fase, busca-se identificar brechas na rede interna que possam ser exploradas posteriormente pelo pentester. As seguintes vulnerabilidades são comumente encontradas ao realizar varreduras de vulnerabilidade:

* Identificação de configurações incorretas, como senhas padrão e permissões fracas
* Detecção de software e sistemas operacionais desatualizados
* Identificação do uso de serviços de rede inseguros
* Métodos de criptografia fracos



#### Ferramentas

Durante esta fase foram usadas as seguintes ferramentas:

* Nessus
* QualysGuard
* Metasploit
* Nikto
* InsightVM



***



### Avaliação Manual

Durante a avaliação manual, os pentesters da Vantico analisam recursos específicos que foram identificados. Na maioria dos casos, os pentesters se concentram em serviços visivelmente abertos:

* Servidores Web/FTP/E-mail/DNS
* Servidores Active Directory (AD) e todos os clientes associados
* Controladores de Domínio (DC)
* Dispositivos conectados à rede
* Servidores SMB e servidores de arquivos
* Outros serviços configurados no intervalo de endereços IP internos



### Ambientes de Active Directory (Windows)

**AD (Active Directory)** é uma solução de gerenciamento de identidades e acessos. As organizações utilizam esse serviço em redes de domínio Windows e também em outros sistemas operacionais.

Dependendo da configuração e do nível de correção (patch level), um pentester pode encontrar uma forma de assumir o controle da rede corporativa comprometendo o Controlador de Domínio (DC).

Algumas áreas-chave nas quais os pentesters da Vantico podem se concentrar durante testes em Active Directory incluem:

* Políticas de senha fracas
* Protocolos antigos ou vulneráveis
* Vulnerabilidades em Kerberos
* Uso de credenciais em cache ou em texto claro (cleartext)
* Relações de confiança mal configuradas
* Permissões mal configuradas em ACDS



### Testes de SMB

O Server Message Block (SMB) é um protocolo de comunicação que permite a interação entre computadores e dispositivos em uma rede. O SMB é comumente utilizado para compartilhamento de arquivos, acesso a impressoras e serviços de domínio.

Os pentesters da Vantico fazem a enumeração de servidores SMB e tentam explorar vulnerabilidades conhecidas, como:

* Assinatura de mensagens SMB desativada
* Falta de patches críticos
* Sessões nulas (null sessions)
* Compartilhamentos de arquivos SMB com autenticação fraca ou ausente
* Ataques de retransmissão SMB (SMB relay)
* Criptografia SMB insegura



### Servidores Web e FTP

Servidores web podem ser alvo de ataques de desfiguração (defacement) ou ser usados como ponto de partida para ataques adicionais contra hosts locais ao próprio servidor web.

Os pentesters da Vantico realizam varreduras em todos os servidores web e FTP da rede interna, em busca de possíveis explorações e vulnerabilidades, tais como:

* Política de correções (patching) deficiente
* Instalações padrão
* Credenciais inseguras



### Dispositivos Conectados à Rede

Impressoras dentro de redes corporativas podem ser compartilhadas com toda a organização e podem ser membros de uma rede AD. Esses dispositivos podem usar credenciais padrão inseguras ou ser vulneráveis a ataques de aplicação web.

Telefones VOIP são comumente encontrados em redes internas e podem ser vulneráveis a configurações incorretas, falhas em SIP ou firmware desatualizado que permita execução remota de código (RCE).

Os pentesters da Vantico testam impressoras e telefones contra todos os ataques comuns e verificam se usam credenciais seguras.



### Quebra de Senhas

Durante uma avaliação de AD, um pentester pode realizar quebra de senhas offline (offline password cracking) contra hashes obtidos durante o engajamento. Algumas técnicas comuns para obter hashes incluem:

* Ataques de envenenamento (poisoning) de LLMNR/NBNS
* Extração de bases NTDS.dit
* Realização de ataques de Kerberoasting
* Execução de ataques de AS-REP roasting
* Extração de bancos de dados SAM
* Realização de ataques com Mimikatz

A quebra de senhas permite que os pentesters da Vantico elevem privilégios e se movimentem lateralmente dentro da rede.



#### Ferramentas

Durante esta fase foram usadas as seguintes ferramentas:

* Ettercap
* Metasploit
* Nmap
* Responder
* Impacket















