# Low Hanging Fruits 2

O pentest vai irá passar pelos seguintes estágios:

* [Reconhecimento](low-hanging-fruits-2.md#reconhecimento)
* [Descoberta de serviços](low-hanging-fruits-2.md#descobertas-de-servicos)
* teste2



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

Depois de buscar por todas as informações disponíveis, passa agora para uma fase mais objetiva no alvo, buscando testes como [Port Scans](low-hanging-fruits-2.md#port-scan), Investigações mais profundas.

#### Ferramentas

* Nmap
* Aquatone
* EyeWitness
* testssl.sh



### Port Scan

Os pentesters podem performar uma busca completa pelo range de IPs da empresa a fim de identificar serviços possivelmente vulneráveis funcionando, tais como:

* Firewall
* Web Server
* FTP



***



















