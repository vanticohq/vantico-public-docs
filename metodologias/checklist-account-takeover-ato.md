---
description: >-
  Uma checklist com verificações de práticas para organizações prevenirem
  Account Takeover
---

# Checklist Account Takeover (ATO)

## Infraestrutura

Sistemas back-end em que confiamos para detecção e mitigação

* [ ] Rate Limit de forma geral
* [ ] Eventos dos usuários / Logs autenticadas
* [ ] Identificação de dispositivo (Cookie)
* [ ] Impressão digital do navegador (Sem cookie)
  * [ ] Não misture com anúncios infra
* [ ] Verificação do dispositivo (Confirmação por e-mail, SMS, correio)
* [ ] Sessão do cliente, fluxos de redefinição de senha (Backend)
* [ ] Link Shim
* [ ] Pipeline de credenciais vazadas (Backend)
  * [ ] Coleta (Pastebin, torrents, etc)
  * [ ] Dark Web e Underground
  * [ ] Dumps acessíveis periodicamente

***



## Indicadores e Recursos

Esta seção descreve dados úteis que muitas vezes precisam ser adquiridos externamente. Eles podem ser usados na classificação automatizada ou para aprimorar fluxos de investigação com informações correlacionadas.

* [ ] Proxies conhecidos, Tor, VPS e colocation
* [ ] Observado como malicioso ou comprometido (Pago)
* [ ] Credenciais vazadas conhecidas
* [ ] Troca recente de SIM
* [ ] Inteligência de domínio
  * [ ] Novos domínios
  * [ ] Descartáveis
  * [ ] Anteriormente afetados
* [ ] Verificação de endereço
* [ ] Verificação celular (Detecção de VoIP)

***



## Produto / UX

Todas as experiências voltadas para o usuário para ajudar a reduzir riscos dentro de um produto.

* [ ] Opções de MFA
  * [ ] Chaves de segurança, MFA, SMS, códigos de backup, etc
* [ ] Base de conhecimento e autoatendimento
  * [ ] Redução da necessidade de contato com o suporte para dúvidas
* [ ] Link Shim
  * [ ] Permite desativar links externos quando copiados, enviados por e-mail ou retirados da plataforma
  * [ ] Permite mensagens de aviso antes de sair da plataforma
* [ ] Escalação de vítimas e testemunhas (Denunciar abuso)
  * [ ] Onde as vítimas relatam o problema
  * [ ] Onde testemunhas de abuso relatam impactos fora da plataforma
* [ ] Fluxos forçados de redefinição de sneha
  * [ ] Solicitar retroativamente que os usuários alterem senhas vazadas
    * [ ] Clientes existentes podem ter senhas fracas
  * [ ] Lidar com novos clientes encontrados em um backend de credenciais vazadas
    * [ ] Novas credenciais vazadas levarão a uma necessidade frequente de alteração de senhas
  * [ ] Redefinir a senha para seu e-mail
    * [ ] Algumas investigações indicarão que o e-mail do cliente está comprometido, e não a senha
  * [ ] Reativação da conta
    * [ ] Fluxos de autoatendimento para restaurar o acesso após intervenção
  * [ ] Aplicação da força da senha para evitar senhas fracas no futuro
    * [ ] Novo registro
    * [ ] Alteração de senhas
    * [ ] Credenciais vazadas/novamente fracas
  * [ ] Alertas no console do desenvolvedor com uma mensagem de aviso
    * [ ] Exemplo: Facebook
  * [ ] Fluxos de trabalho de verificação/desafio
    * [ ] Quando você não tem certeza da localização ou dispositivo do cliente
    * [ ] SMS
    * [ ] Email
    * [ ] Conhecimento da identidade/conta
    * [ ] Envio de ID
    * [ ] CAPTCHA
  * [ ] Detecção de sessão roubada
    * [ ] Exemplo: [Capturando cookies comprometidos](https://slack.engineering/catching-compromised-cookies/)

***



## Atendimento ao cliente

Interações operacionais de atendimento ao cliente (tickets de suporte). As equipes de suporte frequentemente escalam abusos para a engenharia e têm a melhor visibilidade sobre o que está ou não funcionando.

* [ ] Linguagem organizacional padrão
  * [ ] O que conta como um ATO?&#x20;
* [ ] Métricas / KPI
  * [ ] Monitoramento do aumento ou redução de abusos
* [ ] Escalação de IR
  * [ ] Playbooks/planos para criar interrupções ou envolver recurso de engenharia
* [ ] Fluxos de redefinição (Frontends administrativos)
  * [ ] Capacitando operações escaláveis para mitigar cenários de abusos

***



## Investigaçõe e Respostas

Haverá análises profundas periódicas sobre ataques de ATO para entender "o que aconteceu?". Esta seção se refere a essa abordagem de trabalho.

* [ ] Autenticações podem ser pesquisadas por dispositivos, IP, User Agent
  * [ ] Pesquisas podem pivotar: Dispositivos para IP, IP para dispositivos, etc
  * [ ] Bônus: Ações/eventos são pesquisáveis
  * [ ] Bônus: Todas as rotas/endpoints são pesquisáveis
* [ ] Ferramentas para redefinir em massa contas que atendem a critérios
* [ ] Ferramentas para reverter transações/alterações que atendem a critérios

***



## Automação

Unindo tudo para os sistemas operacionais de ATO. O tempo de engenharia é o menos escalável, o tempo de suporte ao cliente é mais escalável, e sistemas totalmente automatizados são os mais escaláveis.

* [ ] Atendimento ao cliente classifica casos de abuso
* [ ] Sistema de IA classificam eventos de autenticação
* [ ] Casos suspeitos empurram os clientes para verificar a aitvidade
* [ ] Reuniões XFN entre grupos para melhorar sistematicamente o combate a abusos

***



## [Anti-Pishing](https://vantico.com.br/us/praticas-para-prevencao-ataques-de-e-mail-spoofing/)

Aumentando a proteção contra ataques triviais de roubo de credenciais, que causam os maiores problemas para organizações despreparadas.

* [ ] SPF / DMARC / DKIM
* [ ] Proteção de marca (varredura na internet para detectar falsificação da sua marca)
* [ ] Spoofing e relatórios de pishing de clientes
* [ ] Monitoramento de lojas de aplicativos
* [ ] Remoção de domínios/ISPs
* [ ] Listas de bloqueio do navegador
* [ ] Referenciadores, hotlinks, vazamentos de adversários

































