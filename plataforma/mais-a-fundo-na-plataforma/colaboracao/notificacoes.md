---
description: Explore as notificações do Vantico.
---

# Notificações

{% hint style="info" %}
Você pode gerenciar notificações para testes e descobertas específicas.
{% endhint %}



Por padrão, você recebe notificações sobre algumas atividades relacionadas à sua organização e pentests – tanto por e-mail quanto no aplicativo Vantico. Se você não estiver recebendo notificações por e-mail, consulte nossas dicas de solução de problemas.



**Veja exemplos de atividades.**

Você é notificado quando alguém:

* Postou uma atualização para um pentest
* Reportou uma vulnerabilidade
* Alterou o status de uma vulnerabilidade

Sua função de usuário determina quais notificações você receberá.



**Gerenciar notificações de Pentest**

Ao colaborar em um pentest, você recebe notificações dependendo de suas preferências de notificação.

Na página do pentest, selecione o ícone de sino Bell icon e defina sua preferência:

* **Notificações sobre todas as atividades**, a menos que você tenha deixado de seguir explicitamente uma descoberta. Esta é a opção padrão.
* **Notificações sobre @ menções e descobertas das quais você participa**
* **Silenciar notificações, exceto nas descobertas que você segue**

<figure><img src="../../../.gitbook/assets/36.png" alt=""><figcaption></figcaption></figure>

**Solucionar problemas de notificações por e-mail**

Você não está recebendo e-mails do Vantico

Faça o seguinte:

* Verifique com seu administrador de TI se o domínio de e-mail vantico.com.br:
  * Não está incluído na lista de remetentes bloqueados.
  * Não aciona uma rejeição severa do Sender Policy Framework (SPF). Esta falha ocorre quando o servidor de e-mail do destinatário rejeita e-mails de endereços IP não especificados no registro SPF.
* Verifique os filtros da sua caixa de correio. Verifique se as regras que você ativou não afetam os e-mails do domínio de e-mail vantico.com.br.
* Verifique se os e-mails do Vantico não estão sendo marcados como spam ou lixo eletrônico.
* Certifique-se de confirmar seu endereço de e-mail no Vantico. Para fazer isso, clique no link do convite por e-mail.



**Você está recebendo e-mails com atraso**

Isso pode acontecer porque sua organização ativou a grey-list para e-mails. Para remediar isso, adicione o domínio de e-mail vantico.com.br à lista de permissões.

Consulte a documentação do seu sistema de gerenciamento de e-mail para obter instruções. Por exemplo, leia como configurar remetentes permitidos no Mimecast.
