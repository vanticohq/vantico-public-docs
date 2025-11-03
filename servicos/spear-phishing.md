# Spear Phishing

Se você chegou até aqui, é porque decidiu participar, ou está considerando participar de uma campanha de phishing conosco. O próximo passo será desenvolvermos juntos um modelo de e-mail e uma página de destino personalizados, feitos sob medida para enganar sua equipe a nos fornecer suas credenciais, simulando uma tentativa de ataque real. Mas antes disso, há algumas preparações a serem feitas.

## Incluir nossa campanha de phishing na lista de permissões

**Por que incluir na lista de permissões?**

Em um ataque de phishing real, é evidente que você não permitiria que os e-mails do invasor passassem pelo filtro de segurança. No entanto, em uma simulação controlada, a finalidade é totalmente diferente. Ao incluir nossa campanha na lista de permissões, garantimos que os e-mails cheguem aos destinatários previstos, possibilitando uma avaliação precisa do comportamento dos usuários. Dessa forma, o teste mede a conscientização e a resposta da equipe, e não a eficiência das suas ferramentas de bloqueio de e-mails e gateway.



## Filtro de Spam

#### O que é o "Filtro Anti-spam"?

É o sistema que analisa e-mails para decidir se são legítimos ou lixo (spam), e os coloca na caixa de entrada, lixo ou quarentena. Funciona durante a verificação dos e-mails e usa regras e checagens automáticas para marcar mensagens suspeitas.

**Por que ajustar em uma simulação de Phishing?**

Se o filtro marcar os e-mails de simulação de phishing como spam e os mover para a lixeira ou quarentena, os usuários não verão a campanha, o que impede o teste de medir o comportamento real diante de uma mensagem suspeita. Por isso, pode ser necessário criar uma exceção controlada, permitindo que os e-mails da simulação cheguem até a caixa de entrada do grupo de teste. Assim, é possível avaliar como os colaboradores identificam e reagem ao e-mail malicioso sem alterar a proteção do restante da organização.

#### Como configurar?

1. Faça login em [https://security.microsoft.com/](https://security.microsoft.com/) com uma conta que tenha Permissões de Administrador.

1.1 Acesse o grupo **"Email & Colaboração" \[1]** -> **"Políticas e regras \[2]"**:

<figure><img src="../.gitbook/assets/unknown (18).png" alt=""><figcaption></figcaption></figure>

2. Ainda em **"Políticas e Regras \[2]"**, vá em **"Políticas de ameaças \[3]"**:

<figure><img src="../.gitbook/assets/unknown (20).png" alt=""><figcaption></figcaption></figure>

3. Nesta tela serão exibidas as políticas e regras configuradas no painel. Acessaremos a opção **“AntiSpam \[4]”**, que se encontra no grupo Políticas, conforme a imagem:

<figure><img src="../.gitbook/assets/unknown (21).png" alt=""><figcaption></figcaption></figure>

4. Após isso, clique em **“Política AntiSpam de entrada (Padrão) \[5]”**:

<figure><img src="../.gitbook/assets/unknown (22).png" alt=""><figcaption></figcaption></figure>

5. Ao clicar, abrirá uma página à direita, navegue até o final da página, e clique em **“Editar remetentes e domínios permitidos e bloqueados \[6]”**:

<figure><img src="../.gitbook/assets/unknown (23).png" alt=""><figcaption></figcaption></figure>

6. Após isso, vá em **"Domínios"** -> **"Mostrar domínios \[7]"**:

<figure><img src="../.gitbook/assets/unknown (26).png" alt=""><figcaption></figcaption></figure>

7. Adicione os Domínios necessários em **"Domínios"** -> **"Inserir domínio personalizado \[8]"** e depois clique em **"Adicionar domínios"**:

<figure><img src="../.gitbook/assets/unknown (27).png" alt=""><figcaption></figcaption></figure>



## Política de entrega avançada

#### O que é a Política de entrega avançada?

A política de entrega avançada é uma configuração que cria um caminho especial para certas mensagens, decidindo como e onde elas chegam (por exemplo, entregar direto na caixa de entrada ou usar um conector diferente). Serve para dar tratamento específico a remetentes ou domínios sem mudar as regras gerais de segurança.

**Por que ajustar em uma simulação de Phishing?**\
Porque a entrega avançada garante que as mensagens de simulação de phishing sigam exatamente o fluxo desejado (evitando alterações indesejadas nos cabeçalhos ou roteamento), isso é importante quando o provedor da simulação envia por conectores ou IPs específicos. Aplicada com escopo restrito, ela permite testar cenários de entrega realistas sem comprometer as defesas.

#### Como configurar?

1. Faça login em [https://security.microsoft.com/](https://security.microsoft.com/) com uma conta que tenha Permissões de **Administrador**.

1.1 Acesse o grupo **"Email & Colaboração \[1]"** -> **"Políticas e Regras \[2]"**:

<figure><img src="../.gitbook/assets/unknown (28).png" alt=""><figcaption></figcaption></figure>

2. Ainda em **"Políticas e Regras \[2**]**"**, vá em **"Políticas de ameaças \[3]"**:

<figure><img src="../.gitbook/assets/unknown (30).png" alt=""><figcaption></figcaption></figure>

3. Nesta tela serão exibidas as políticas e regras configuradas no painel. Acessaremos a opção **“Entrega Avançada \[4]”**, que se encontra no grupo Regras, conforme a imagem:

<figure><img src="../.gitbook/assets/unknown (32).png" alt=""><figcaption></figcaption></figure>

4. Ao entrar, clique em **"Simulação de Phishing \[5]"** e após isso, **"Add \[6]"**:

<figure><img src="../.gitbook/assets/unknown (33).png" alt=""><figcaption></figcaption></figure>

5. Adicione os **"Domínios \[7]"** e **"IPs \[8]"** necessários, após adicionar, clique em **"Salvar \[9]"**:

<figure><img src="../.gitbook/assets/unknown (34).png" alt=""><figcaption></figcaption></figure>

6. Após Finalizar, você deverá ver uma Tela com os **"Domínios e IPs salvos \[10]**":

<figure><img src="../.gitbook/assets/unknown (36).png" alt=""><figcaption></figcaption></figure>



## Tenant Allow Block List

#### O que é "Tenant Allow Block List"?

É uma lista no nível da organização onde os administradores definem se e-mails de certos remetentes, domínios ou endereços IP devem ser entregues ou bloqueados, ela age no início do processo de recebimento de e-mails e pode substituir as checagens normais de spam e vírus.

**Por que ajustar em uma simulação de Phishing?**\
Usado para garantir que remetentes externos de fornecedores de simulação não sejam rejeitados antes de chegar ao fluxo de avaliação, isso evita falsos negativos (campanhas que falham por bloqueio) e permite validar entregabilidade e métricas da campanha. Faça a alteração de forma limitada e temporária para não criar exceções permanentes na proteção.

#### Como configurar?

1. Faça login em [https://security.microsoft.com/](https://security.microsoft.com/) com uma conta que tenha Permissões de **Administrador**.

1.1 Acesse o grupo **"Email & Colaboração \[1]"** -> **"Políticas e Regras \[2]"**:

<figure><img src="../.gitbook/assets/unknown (37).png" alt=""><figcaption></figcaption></figure>

2. Ainda em **"Políticas e Regras \[2]"**, vá em **"Políticas de ameaças \[3]"**:

<figure><img src="../.gitbook/assets/unknown (38).png" alt=""><figcaption></figcaption></figure>

3. Nesta tela serão exibidas as políticas e regras configuradas no painel. Acessaremos a opção **“Listas de Permissões/Bloqueios do Locatário \[4]”**, que se encontra no grupo Regras, conforme a imagem:

<figure><img src="../.gitbook/assets/unknown (39).png" alt=""><figcaption></figcaption></figure>

4. Ao entrar, clique em **"Domains & Addresses \[5]"** e depois em **"Adicionar -> Block \[6]"**:

<figure><img src="../.gitbook/assets/unknown (40).png" alt=""><figcaption></figcaption></figure>

5. Após clicar em **"Block"**, você deverá fornecer os Domínios **"Adicionar Domínios e Endereços \[7]"** necessários e a quantidade de dias **"Remove Block Entry After \[8]"** após isso, clique em **"Salvar"**:

<figure><img src="../.gitbook/assets/unknown (41).png" alt=""><figcaption></figcaption></figure>

## Pré-lançamento: Testando a campanha

Com a sua ajuda, vamos testar a campanha de ponta a ponta duas vezes:

1. **Uma vez logo após termos criado e configurado.**
2. Logo antes de ela entrar no ar.

Enviaremos um e-mail e pediremos que você complete todo o processo, inserindo credenciais falsas (ou reais, fica a sua escolha). Se houver problemas, será preciso atrasar o lançamento da campanha.



## Durante a campanha

Observe como sua equipe reage à campanha e anote algumas de suas reações. Se desejar, você também pode nos informar! Adoramos ouvir os resultados do nosso trabalho.



## Pós-campanha

Após cerca de 24 horas, a maioria das pessoas terá tido a chance de interagir com a campanha de alguma forma. O boca a boca se espalha rapidamente e seus funcionários mais alertas provavelmente já informaram outros sobre o ataque de phishing (o que é bom), significa que chegou a hora de encerrar.

Com os testes finalizados, é importante remover a lista de permissões que você adicionou anteriormente.



## Debriefing interno

Engenharia social é um tópico sensível, enquanto os computadores não se importam em serem hackeados, as pessoas podem ter uma reação negativa ao cair em uma campanha de phishing. É vital que você reforce a todos que se sentiram mal e mostre a campanha de forma positiva, agradecendo às pessoas por participarem na melhoria da segurança da empresa.

Em nossa experiência, envergonhar ou repreender pessoas que caíram no phishing, tende a piorar sua segurança cibernética. Isso impede que as pessoas relatem incidentes e causa uma visão negativa sobre o treinamento de segurança cibernética. Não queremos trabalhar com empresas que abusam de nossos serviços dessa maneira e nos recusaremos a realizar exercícios de phishing adicionais se encontrarmos qualquer abuso.

Uma discussão aberta com todos os funcionários sobre a campanha pode ser extremamente benéfica. Pergunte (com antecedência) se as pessoas que foram atacadas querem compartilhar seu processo de pensamento sobre porque funcionou com elas. Da mesma forma, peça àqueles que perceberam a fraude para explicar o que os fez desconfiar.

Por fim, peça às pessoas que foram afetadas pelo phishing para mudar suas senhas.

