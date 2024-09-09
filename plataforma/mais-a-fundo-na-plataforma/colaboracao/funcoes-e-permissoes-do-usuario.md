---
description: Saiba mais sobre as funções do usuário e as permissões associadas.
---

# Funções e permissões do usuário

{% hint style="info" %}
Dependendo da sua função, você pode ter acesso a uma organização, a testes de invasão específicos ou a ambos.
{% endhint %}



Funções e Permissões Principais

{% tabs %}
{% tab title="Funções do Usuário" %}
**Nível do Pentest:**

* Membro da equipe Pentest:
  * Colabora em um pentest específico.
  * Não tem acesso aos usuários e configurações da organização, a menos que o usuário também seja proprietário ou membro da organização.

***

**Nível de Organização:**

* Proprietário da organização:
  * Pode criar ativos e testes de invasão.
  * Gerencia usuários e configurações da organização.
  * Pode criar e gerenciar grupos.
  * Não é possível colaborar em pentests específicos, a menos que o usuário também seja membro da equipe do Pentest nesses pentests.
* Membro da Organização:
  * Pode criar ativos e testes de invasão.
  * Pode visualizar usuários e configurações da organização.
  * Pode ver os grupos dos quais são membros.
  * Não é possível colaborar em pentests específicos, a menos que o usuário também seja membro da equipe do Pentest nesses pentests.

***

**Pentest + Nível de Organização:**

* Proprietário da organização + membro da equipe do Pentest (em pentests específicos)
* Membro da Organização + Membro da Equipe Pentest (em pentests específicos)
{% endtab %}

{% tab title="Função do Pentester" %}
**Pentesters Vantico:**

* Pentester: Conclui testes de pentes para clientes Vantico.
* Líder: Lidera um grupo de Vantico Pentesters para completar um pentest completo.
* Coordenador: Lidera um grupo de Vantico Pentesters para concluir um teste Agile.

***

**Pentesters de clientes:**

* Pentester interno: realiza pentests para sua organização na plataforma de gerenciamento Vantico Pentest.
{% endtab %}

{% tab title="Funções da Administração" %}
**Equipe Vantico:** Tem acesso administrativo aos seus pentests e organização.
{% endtab %}
{% endtabs %}



**Membro da equipe Pentest**

Um membro da equipe Pentest é um representante do cliente (organização) durante um pentest específico. Na IU, você vê esta função como “Membro da equipe”.

* Um membro da equipe Pentest não precisa ser proprietário ou membro da organização.
* Quando um proprietário da organização convida um usuário para uma organização, o usuário também se torna um membro da equipe do Pentest em todos os pentests da organização.
  * O proprietário da organização pode remover um membro da equipe do Pentest de todos os pentests em que colabora.
  * Qualquer membro da equipe do Pentest pode adicionar usuários a um pentest específico ou removê-los.

Um membro da equipe do Pentest tem acesso a um pentest específico com as seguintes permissões:

* Visualize e edite detalhes do pentest.
* Gerenciar descobertas para um pentest.
* Colabore em um pentest no aplicativo Vantico e no Slack. Gerencie usuários para um pentest.
* Veja atualizações de atividades de pentest e atualizações de pentester.
* Gerencie integrações para um pentest: Jira e GitHub.

Um membro da equipe Pentest não tem acesso a nenhuma informação relacionada à organização, a menos que também seja proprietário ou membro da organização.



**Veja mais:**

Um membro da equipe Pentest **não tem acesso** às seguintes páginas, a menos que também seja proprietário ou membro da organização:

* **Ativos**
* **Pentests (exceto pentests nos quais eles colaboram)**
* **Descobertas**
* **Percepções**
* **Pessoas**
* **Créditos**
* **Integrações**
* **Configurações**



**Funções da Organização**

Quando um cliente inicia sua jornada com a Vantico, adicionamos um proprietário da organização que convida outros usuários. Aqui está uma visão geral das funções e permissões da organização.

| Permissão                                                                                                    | Membro da Organização | Dono da Organização |
| ------------------------------------------------------------------------------------------------------------ | --------------------- | ------------------- |
| Crie ativos e pentests, edite ativos                                                                         | ✓                     | ✓                   |
| Alterar o grupo ao qual um ativo está associado                                                              | —                     | ✓                   |
| Veja todas as descobertas relatadas em uma organização na página Descobertas, dentro das permissões do grupo | ✓                     | ✓                   |
| Visualize os usuários da organização e os colaboradores do pentest na página Pessoas                         | ✓                     | ✓                   |
| Gerenciar integrações para uma organização                                                                   | ✓                     | ✓                   |
| Edite o perfil da organização                                                                                | ✓                     | ✓                   |
| Veja o livro de créditos                                                                                     | ✓                     | ✓                   |
| Ver a página Insights                                                                                        | ✓                     | ✓                   |
| Gerenciar usuários de uma organização                                                                        | —                     | ✓                   |
| Criar e gerenciar grupos                                                                                     | —                     | ✓                   |
| Gerencie as configurações de segurança de uma organização: autenticação de dois fatores e SAML               | —                     | ✓                   |
| Habilite relatórios de marca conjunta (para parceiros Vantico)                                               | —                     | ✓                   |



**Dono da Organização**

Um proprietário da organização é o administrador de uma organização do cliente no aplicativo Vantico. Na IU, você vê esta função como “Proprietário”.

Um proprietário da organização tem as seguintes **permissões**:

* Crie ativos e testes de invasão, edite ativos.
* Gerencie usuários de uma organização na página **Pessoas**:
  * Convide e remova usuários.
  * Alterne as funções do usuário.
  * Veja os endereços de e-mail dos usuários.
  * Remova os membros da equipe do Pentest de todos os pentests em que colaboram.
* Crie, edite e gerencie grupos.
* Gerencie as configurações de segurança de uma organização: autenticação de dois fatores e SAML.
* Habilite relatórios de marca conjunta (para parceiros Vantico).
* Gerenciar integrações para uma organização.
* Edite o perfil da organização.
* Veja o livro de créditos.
* Veja a página Insights.

O proprietário da organização também pode ser um membro da equipe do Pentest.





**Membro da Organização**

Um membro da organização é um representante do cliente que gerencia testes de invasão e ativos de sua organização na plataforma Vantico, mas tem menos permissões em comparação com um proprietário da organização. Na IU, você vê essa função como “Membro”.

Um membro da organização tem as seguintes **permissões**:

* Crie ativos e testes de invasão, edite ativos, dentro das permissões do grupo.
* Visualize usuários e colaboradores do pentest na página Pessoas.
* Gerenciar integrações para uma organização.
* Edite o perfil da organização.
* Veja o livro de créditos.
* Veja a página Insights.

Um Membro da Organização também pode ser um Membro da Equipe Pentest.





**Pentesters Vantico**

Quando você executa pentests usando a plataforma Vantico Pentest as a Service (PtaaS), os pentesters Vantico participam do processo. Este grupo inclui as seguintes funções:,

* Pentester
* Líder
* Coordenador





**Pentester**

Um Pentester é um pentester Vantico que realiza testes de pentes para clientes Vantico.

As responsabilidades de um Pentester incluem:

* Teste minuciosamente um ativo em busca de vulnerabilidades com base no escopo e nos requisitos do pentest.
* Envie vulnerabilidades (descobertas) e forneça dicas de correção.
* Teste novamente as descobertas que o cliente corrigiu em um pentest.
* Colabore com o cliente durante um pentest.

Alguns pentesters Vantico podem ser líderes em um teste, pentester em um segundo teste e possivelmente nenhuma função e nenhum envolvimento em seus outros pentesters.





**Líder**

Um líder de pentest é um pentester Vantico que lidera outros pentesters Vantico em seus esforços para concluir um Pentest Completo. Um líder de pentest também elabora um relatório de pentest.

Para pentests Agile, a função correspondente é Coordenador.





**Coordenador**

Um coordenador de pentest é um pentester Vantico que lidera outros pentesters Vantico em seus esforços para concluir um pentest Agile.

Para pentests completos, a função correspondente é Líder.





**Pentester interno**

Um pentester interno é um pentester convidado por um cliente (organização) para realizar testes de pentes internos na Vantico Pentest Management Platform (PMP). Uma função de pentester interno tem os mesmos privilégios de um membro da equipe de pentest, com acesso adicional à funcionalidade de pentester.

Um cliente pode convidar pentesters de sua organização, de uma empresa terceirizada ou de ambas para realizar testes de pentes internos na Vantico Pentest Management Platform (PMP).

Aprenda como realizar um pentest interno.





**Equipe Vantico**

Membros selecionados da equipe Vantico têm acesso administrativo à sua organização e aos testes de invasão. Se necessário, eles podem ajudá-lo:

* Gerenciar usuários em sua organização
* Gerencie o trabalho em seus testes de invasão
