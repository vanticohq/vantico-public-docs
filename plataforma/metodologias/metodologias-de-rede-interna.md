---
description: Revise as metodologias de pentest Vantico para redes internas.
---

# Metodologias de Rede Interna

O teste de penetração de rede interna é um processo no qual um testador usa ataques simulados para identificar possíveis vulnerabilidades de segurança em uma rede interna.



Seguimos uma metodologia padrão do setor baseada principalmente no Manual de Metodologia de Teste de Segurança de Código Aberto (OSSTMM).



<figure><img src="../../.gitbook/assets/rede interna.png" alt=""><figcaption></figcaption></figure>

O teste de penetração de uma rede interna inclui as seguintes etapas:

* Reconhecimento de escopo alvo&#x20;
* Descoberta de serviço&#x20;
* Verificações de vulnerabilidade&#x20;
* Avaliação manual&#x20;
* Testes adicionais
* Relatórios, triagem e novos testes



> Nota:
>
> As ferramentas que nossos pentesters usam durante cada fase de teste podem variar de teste para teste.



A equipe de avaliação de segurança da Vantico realiza testes sem o seguinte, a menos que seja exigido como parte do escopo do pentest:

* Diagramas detalhados de rede ou infraestrutura&#x20;
* Quaisquer contas ou informações adicionais do usuário&#x20;

No entanto, você pode adicionar diagramas de rede e outros detalhes ao **descrever seu ativo.**



**Pré-requisitos**

Como os pentesters Vantico executam testes de pentes para redes internas remotamente, eles precisam:

* Acesso à rede corporativa interna através de uma conexão VPN estável&#x20;
* Um servidor Linux leve dentro da rede que serve como uma caixa de salto a partir da qual os pentesters podem verificar e testar a rede interna durante a avaliação

Dependendo da configuração da sua rede, faça o seguinte:

*   Para redes executadas em máquinas Amazon Web Services (AWS):&#x20;

    * Crie uma máquina virtual (VM) Kali dentro da AWS.&#x20;
    * Configure o acesso SSH baseado em chave para cada pentester.&#x20;

    Para redes que não usam uma configuração de rede na nuvem:

    * Baixe uma imagem Kali VMWare/VirtualBox.&#x20;
    * Configure o acesso SSH baseado em chave para cada pentester.



> Nota:
>
> Os recursos de sistema recomendados para a imagem virtual (VMWare, VirtualBox ou AWS) devem ser pelo menos:
>
> * 2 CPUs virtuais alocadas&#x20;
> * 8 GB de RAM&#x20;
> * 20 GB de espaço em disco&#x20;
>
> Os pentesters também precisam de acesso Root ao Kali VM, que é obrigatório.



**Reconhecimento do Escopo Alvo**

Os pentesters Vantico procuram todas as informações que um usuário mal-intencionado possa encontrar. Por exemplo, para se conectar à Internet, você normalmente compartilha algumas informações:

* Para receber e-mail, você precisa postar um endereço de servidor de e-mail.&#x20;
* Para configurar um servidor web, você precisa postar seu URL e muito mais.

Um invasor pode ter vários caminhos de exploração. Os pentesters Cobalt exploram todos esses caminhos para coletar informações que um invasor poderia usar para obter acesso a recursos internos, como:

* Credenciais de força bruta usando formatos de e-mail corporativos descobertos&#x20;
* Construindo dicionários de senha contendo informações comerciais públicas do site corporativo

Durante a fase inicial de testes, os pentesters determinam quais informações estão disponíveis publicamente. Eles examinam o seguinte:

*
