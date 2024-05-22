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



Fase de Reconhecimento

* Grande: Uma empresa com múltiplos domínios
* Média: Um único domínio
* Pequena: Um único website



Escopo Grande

* [ ] Busque ASN para encontrar até onde vai o IP (amass, anslookup, metabigor, bgp)
* [ ] Analise as últimas aquisições
* [ ] Consiga as relações dos registrantes (viewdns)
* [ ] Vá para o escopo médio para cada domínio

Escopo Médio

* [ ] Enumere os subdomínios (amass ou subfinder)
* [ ] Força Bruta nos subdomínios (puredns com wordlist)
* [ ] Identifique subdomínios ativos (httpx)
* [ ] Aquisição de subdomínios (nuclei-takeovers)
* [ ] Procure por ativos na nuvem (cloudenum)
* [ ] Pesquisa no Shodan
* [ ] Transfer Zone
* [ ] Pegar capturas de tela (gowitness, webscreenshot, aquatone)

Escopo Pequeno

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



Rede

* [ ] Verifique se pacotes ICMP estão permitidos
* [ ] Verifique as políticas DMARC/SPF (spoofcheck)
* [ ] Abra portas com o Shodan
* [ ] Port Scan em todas as portas
* [ ] Verifique as portas UDP (nmap)
* [ ] Teste SSL (testssl)
* [ ] Se possuir credenciais, tente pulverização de senhas em todos os serviços descobertos



Preparação

* [ ] Estude a estrutura do site
* [ ] Faça uma lista de todos os possíveis testes
* [ ] Entenda sobre o negócio e o que seus clientes precisam
* [ ] Consiga uma lista com todos os ativos (all\_subdomains.txt, live\_subdomains.txt, waybackurls.txt, hidden\_directories.txt, nmap\_results.txt, GitHub\_search.txt, altdns\_subdomain.txt, vulnerable\_links.txt, js\_files.txt)



