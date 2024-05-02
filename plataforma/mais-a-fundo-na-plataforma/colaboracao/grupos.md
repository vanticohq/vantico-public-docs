---
description: Os grupos fornecem estrutura e controles de acesso flexíveis.
---

# Grupos

{% hint style="info" %}
Como proprietário da organização, você pode gerenciar o acesso aos ativos da sua organização e aos testes e descobertas associados.
{% endhint %}



**Crie um grupo**

Atribua ativos e membros da organização a um grupo:

* Navegue até a página **Pessoas** e depois até a guia **Grupos**.
* Selecione **Criar grupo.**
* A tela **Criar grupo** solicita o seguinte:
  * **Nome do grupo**: configure um nome descritivo para identificar facilmente o grupo.
  * **Descrição**: Adicione informações para descrever melhor o grupo.
  * **Ativos associados**: selecione em uma lista de todos os ativos da sua organização (Observação: os ativos já associados a outro grupo não aparecerão nesta lista).
  * **Membros**: selecione em uma lista de todos os membros da organização em sua organização. Esses usuários terão acesso exclusivo aos ativos associados ao grupo e aos seus testes e descobertas.
    * Os proprietários da organização e a equipe do Vantico não aparecerão nesta lista, mas ainda terão acesso a todos os ativos.
    * Os membros da equipe do Pentest que não fazem parte da sua organização ainda podem ser adicionados manualmente a cada pentest.
* Selecione **Criar Grupo**

<figure><img src="../../../../.gitbook/assets/Groups_CreateForm.png" alt=""><figcaption></figcaption></figure>

**Ver e Gerenciar Grupos**

<figure><img src="../../../../.gitbook/assets/Groups_MainPageandActions.png" alt=""><figcaption></figcaption></figure>

Na página Grupos, você pode:

* Crie um grupo
* Veja todos os grupos da sua organização
* Gerenciar grupos. Selecione o ícone de três pontos em **Ações** e selecione a opção desejada:
  * **Editar** grupo para modificar os detalhes do grupo
  * **Excluir** grupo, se não tiver ativos associados



**Página de detalhes do grupo**

<figure><img src="../../../../.gitbook/assets/Groups_ViewPage.png" alt=""><figcaption></figcaption></figure>

Na página de detalhes do grupo, você pode:

* Ver ativos associados
* Ver membros do grupo
* Editar detalhes do grupo
* Exclua o grupo, se ele não tiver ativos associados



**Atribuindo um grupo a um ativo**

Além de atribuir ativos existentes a um grupo na página Grupos, você pode atribuir um grupo durante a criação ou edição de ativos.

<figure><img src="../../../../.gitbook/assets/CreateNewAsset.png" alt=""><figcaption></figcaption></figure>

* A tela **Ativo** solicitará os detalhes usuais.
* Você também verá um campo **Grupo atribuído**. Por padrão, isso é definido como o grupo ‘Todos os membros da organização’. Selecione no menu suspenso para escolher outro grupo dentro da sua organização.
  * Os **membros da organização** só poderão atribuir grupos dos quais já fazem parte ao criar novos ativos e não terão permissões para reatribuir o grupo depois que o ativo for criado (os proprietários da organização e a equipe do Vantico podem fazer ambos).
* Depois de criado, o ativo e qualquer um de seus testes e descobertas estarão acessíveis ao grupo atribuído.

> Nota:
>
> Atualmente, apenas um grupo pode ser atribuído por ativo.





**Acesso e permissões**

Somente proprietários da organização podem criar, gerenciar e visualizar todos os grupos da organização.

Embora os ativos possam ser associados a grupos específicos e aos seus membros, os proprietários sempre terão acesso a todos os ativos da organização.

Os membros da organização só têm acesso somente leitura aos grupos dos quais são membros.

* Os membros da organização podem visualizar e gerenciar ativos que pertencem aos seus grupos. No entanto, eles não podem reatribuir um grupo de ativos depois que o ativo for criado.
* Os membros da organização podem acessar todos os testes e descobertas que pertencem aos ativos de seus grupos.

Para obter mais informações sobre permissões de usuário, consulte Funções e permissões de usuário.





**Perguntas Frequentes**

Como posso saber qual grupo possui um pentest individual?

* A guia **Colaboradores** do pentest ainda mostrará todos os colaboradores individuais e qualquer grupo do qual eles possam fazer parte.

Todos os colaboradores de um pentest serão transferidos quando eu copiar o pentest?

* Sim. Todos os membros individuais do grupo que possuem o pentest e qualquer membro que não seja do grupo que tenha sido adicionado manualmente anteriormente serão transferidos para o pentest recém-copiado.

Os grupos são necessários?

* Todos os ativos exigirão um grupo atribuído. No entanto, se você planeja não usar esse recurso, poderá atribuir ativos ao grupo padrão **Todos os membros da organização.**
