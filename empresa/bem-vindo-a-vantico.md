# Bem Vindo a Vantico!

Olá e bem-vindo a **Vantico**! Se você está lendo isso, provavelmente acabou de se juntar à família Vantico (ou talvez seja um leitor externo curioso). Tenho certeza de que você está animado para começar e nós também estamos ansiosos para conhecê-lo melhor.

Neste guia você aprenderá o básico sobre a Vantico e conhecerá como trabalhamos, quais ferramentas utilizamos e onde pedir ajuda. Sabemos como é importante começar com o **pé direito** e este guia tem como objetivo capacitá-lo a fazer exatamente isso.



**Breve introdução a Vantico**

Começamos a Vantico como algo divertido de fazer. Sabíamos em que tipo de empresa queríamos trabalhar e nada era adequado para nós, então decidimos tentar nós mesmos. Tendo trabalhado com segurança desde 2021 pelo menos, não vimos muitas mudanças significativas na indústria e sabíamos que ela precisava mudar. Queremos continuar a **inovar** e ajudar a indústria a crescer como um todo, ao mesmo tempo que cuidamos daqueles que nos rodeiam e os ajudamos a prosperar.



**Como é na Vantico?**

Temos uma cultura fácil de lidar. Não nos levamos muito a sério, mas somos **apaixonados** pelo que fazemos. Acreditamos que o que fazemos ajuda pessoas como os clientes de nossos clientes e seus funcionários. Acreditamos em **fazer o que você ama** (é uma de nossas filosofias que você ouvirá muito) e isso significa que você é responsável por si mesmo. Você pode escolher o seu horário, desde que o trabalho seja feito no prazo, seja de **excelente qualidade** e o **cliente fique satisfeito.**

Temos uma cultura estrita de não culpa. Isso vale para outras pessoas da Vantico e nossos clientes. A segurança é **genuinamente difícil** e cabe a nós torná-la um pouco mais fácil, **sem nos exibirmos ou culparmos os outros** pelos problemas de segurança.

Também somos grandes em **ensinar e aprender**. Ninguém sabe tudo e todos (mesmo aqueles que são novos na infosec) têm algo a ensinar. Somos abertos com informações, como pessoas e como empresa. Nós nos esforçamos para ser abertos, mas seguros (outra filosofia), o que significa que tentamos abrir o código-fonte de tudo que não seja confidencial (este Manual, por exemplo)!

Confira também uma descrição mais detalhada de nossos **valores**.



**O que esperar no Primeiro Dia**

O primeiro dia é sobre **aprender e se estabelecer**. Você provavelmente estará lendo isso no primeiro dia. Seu gerente irá ajudá-lo a começar, dando-lhe acesso a ferramentas básicas como **E-mail e Slack.** Você também receberá uma lista do Trello com coisas para fazer. Isto incluirá o acesso aos sistemas e o preenchimento de alguns formulários oficiais.

Você conhecerá muitas pessoas novas, incluindo os fundadores. Serão muitas informações, mas não deixe que isso o sobrecarregue; você não precisa memorizar nada. Vá com calma, continue lendo e reserve um tempo para configurar seu sistema ao seu gosto.

Você também receberá um **“amigo”**, alguém que o ajudará no aprendizado das coisas da Vantico e alguém com quem você poderá conversar sobre qualquer coisa.



**Sistemas Importantes (equipe de prestação de serviços)**

Esta seção fornece um resumo rápido do **hardware e software** que é mais importante para os iniciantes na equipe de prestação de serviços. Uma lista de todos os provedores de serviços terceirizados que usamos pode ser encontrada aqui.

**Hardware**

O laptop e outros hardwares que você usa serão **extremamente importantes**. Oferecemos um subsídio anual de hardware para itens que você possa precisar, incluindo laptop, dock, webcam, headset, periféricos e outros itens para **facilitar seu trabalho**. Você pode escolher seu próprio laptop e outro hardware que mais lhe convier. Geralmente, reembolsaremos os custos de hardware dentro do padrão. Em caso de dúvida, consulte seu gerente antes de comprar.

Com a liberdade de escolha, vem a **responsabilidade**. Você é responsável pela **manutenção e segurança do seu próprio laptop**. No entanto, temos alguns requisitos mínimos de segurança que você pode encontrar na página **Segurança Pessoal**. Planeje que seu laptop dure pelo menos **3 anos.** Isso significa que é altamente recomendável obter garantia de pelo menos 3 anos.

As seguintes especificações de laptop são mínimas recomendadas:

* CPU: Intel i7 ou AMD Ryzen 7&#x20;
* RAM: 16GB&#x20;
* Armazenamento: 500GB SSD&#x20;
* Resolução: 1080p&#x20;
* Porta Ethernet: sim

**Microsoft 365**

Usamos M365 para e-mail, gerenciamento centralizado de identidades, SharePoint para armazenamento de arquivos e Teams apenas para videochamadas externas.

Para conectar o compartilhamento de arquivos para toda a empresa à sua conta, siga estas etapas:

1. Certifique - se de que tenha o OneDrive instalado
2. Siga este link. Isso o levará ao armazenamento de arquivos no SharePoint: https://Vanticocomau.sharepoint.com/Shared%20Documents/Forms/AllItems.aspx
3. Clique no botão **Sincronizar** na parte superior. O OneDrive deve se conectar automaticamente ao SharePoint

**Slack**

Slack é nossa principal plataforma de **comunicação** interna. Tentamos integrar o máximo possível de outros aplicativos ao Slack. Você provavelmente o usará mais do que e-mail.

Depois de ter um endereço de e-mail Vantico, você mesmo pode se inscrever no Slack usando este link: https://join.slack.com/t/Vantico/signup (você deve usar seu endereço de e-mail @Vantico.com.au)

Para obter mais informações sobre o Slack, consulte nosso guia de etiqueta e uso do Slack.

**Chave PGP**

Como normalmente lidamos com dados confidenciais, pedimos a todos os consultores que gerem uma chave PGP vinculada ao seu endereço de e-mail Vantico.com.au para qualquer comunicação confidencial.

* Para Windows você pode usar Kleopatra;
* Para Mac você pode usar GPG Suite;
* Ou você pode usar GnuPG no Linux.

Certifique-se de gerar uma chave de 4.096 bits com os detalhes corretos. Gere um certificado de revogação! Não queremos que ninguém criptografe informações confidenciais com sua chave caso ela tenha sido comprometida! Envie a chave pública e sua impressão digital ao seu gerente para que ele possa adicioná-la à sua assinatura de e-mail.

**Criando um par de chaves: Windows e Mac:**

1. Baixe o conjunto relevante de ferramentas
2. Abra o aplicativo Keychain (Kleopatra/GPG Keychain)
3. Vá para Configurações > Configurar Kleopatra (Mac: Chaveiro GPG > Preferências)
4. Altere o servidor de chaves OpenPGP para “hkps://keyserver.ubuntu.com”
5. Clique em Aplicar/Salvar (Mac: Fechar janela)
6. Selecione Arquivo > Novo Certificado/Nova Chave
7. Digite seu nome e endereço de e-mail Vantico
8. Defina a data de validade para daqui a 10 anos
9. Windows: Caixa de seleção “Proteger a chave gerada com senha”
10. Crie uma senha forte (guarde-a em algum lugar seguro, como seu gerenciador de senhas)
11. Siga as instruções para concluir a configuração

**Criando um certificado revogado**&#x20;

Windows:

1. Clique com o botão direito no seu par de chaves recém-criado no Kleopatra
2. Selecione “Detalhes”
3. Clique em “Gerar certificado de revogação”
4. Salve o certificado em algum lugar seguro e faça backup dele&#x20;

Mac:

1. Clique com o botão direito no par de chaves recém-criado no GPG Keychain
2. Selecione “Criar Certificado Revogado”
3. Salve o certificado em algum lugar seguro e faça backup dele&#x20;

**Publicando seu certificado em um servidor de chaves**&#x20;

Windows e Mac:

1. Clique com o botão direito no par de chaves recém-criado no Kleopatra/GPG Keychain
2. Selecione “Publicar no Servidor” / “Enviar Chave Pública para Servidor Chave”
3. Após alguns minutos, visite https://keyserver.ubuntu.com/
4. Digite “Vantico.com.au” na caixa de pesquisa e clique em “Chave de pesquisa”
5. Confirme se sua chave pública foi carregada com sucesso

**Licenças de software para testes**

Você receberá licenças para as ferramentas usuais, como Burp Suite Professional, Nessus e VMWare Workstation/Fusion.

**Outros hardwares/softwares**

Se você tiver seu hardware/software favorito que gostaria de usar, provavelmente poderemos reembolsá-lo pelo custo. Basta perguntar!

**Formulários e produtos**

Vamos negociar! Envie-nos esses detalhes…

• Declaração de número fiscal

• Escolha padrão de aposentadoria

• Declaração de retenção

• Declaração de variação da taxa do Medicare (opcional)

… e em troca lhe enviaremos:

• Seus próprios cartões de visita

• Adesivos Vantico

• Uma camiseta Vantico

• Um copo de cerveja Vantico

Você já deve ter recebido alguns formulários no Slack para preencher.

Eles cobrem tudo, exceto a declaração de variação da taxa do Medicare. Você pode encontrar esse formulário aqui:
