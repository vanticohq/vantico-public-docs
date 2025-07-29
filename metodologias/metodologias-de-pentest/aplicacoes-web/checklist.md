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



**Low Hanging Fruit - Information Gathering**

* [ ] Encontrar LinkedIn
* [ ] Informações Pastebin e Trello
* [ ] Google Hacking, exemplo: ext:, intext: intitle:
* [ ] Metadados em arquivos
* [ ] Shodan / Censys
* [ ] Busca em certificados (crt.sh)
* [ ] Virus Total
* [ ] DnsDumpster
* [ ] SecurityTrails
* [ ] [email-spoof](https://github.com/vanticohq/email-spoof)
* [ ] Subdominios (subfinder, SecurityTrails, DnsDumpster, crt.sh, Amass)
* [ ] Subdomain Takeover
* [ ] Busca robots.txt e sitemap.xml
* [ ] Busca e-mails (hunter.io, anymailfinder, rocketreach)
* [ ] SpiderFoot
* [ ] Wappalyzer



**Low Hanging Fruit**

* [ ] Ausência de Header
* [ ] Js.map
* [ ] Integrity
* [ ] SSL/TLS
* [ ] Vulnerabilidade da Versão do Server
* [ ] Portas Abertas
* [ ] Nuclei / Katana
* [ ] Política de Senhas Permissivas
* [ ] Mensagem de Erros
* [ ] Utilizar bibliotecas JavaScript desatualizadas
* [ ] Enumeração de Usuário
* [ ] Falsificação de e-mails
* [ ] Sessão antiga não é inválida após o logout
* [ ] Ausência de mecanismo contra força bruta
* [ ] Uso de IDs sequenciais
* [ ] Upload irrestrito de arquivos
* [ ] Registro e monitoramento insuficiente de atividades
* [ ] Negação de serviço através de múltiplas tentativas de login
* [ ] Falta de validação na alteração de dados
* [ ] Validação de input insuficiente
* [ ] Validação de registro de dados pessoais
* [ ] Invalidação do link de redefinição de senha
* [ ] Host header injection
* [ ] Flood de e-mail por meio de redefinição de senha
* [ ] Redirecionamento HTTP para HTTPS
* [ ] Acesso via IP diretamente
* [ ] Aplicação mostrando hash de senhas
* [ ] Verificações no JWT
* [ ] Página web armazenando credenciais sem criptografia
* [ ] Cookie de sessão sem a flag Secure habilitada
* [ ] Cookie de sessão sem a flag HttpOnly habilitada
* [ ] Upload de arquivos
* [ ] Gerenciamento de patch insuficiente
* [ ] Ausência do arquivo robots.txt
* [ ] Ausência de WAF
* [ ] Flood em páginas com brute force
* [ ] Ausência de notifcação por login suspeito
* [ ] Subdomínios apontando para IPs privados
* [ ] CORS Misconfiguration



{% hint style="info" %}
Para mais informações sobre checklist de pentest em aplicações web, consulte:

[Checklist](https://pentestbook.six2dez.com/others/web-checklist)
{% endhint %}

