# Metodologia Red Team e simulação de adversário

A Vantico realizará um exercício de Red Team na organização. Diferentemente de um teste de penetração, o objetivo de um Red Team não é identificar vulnerabilidades, mas alcançar metas pré-definidas. Isso é feito por quaisquer meios necessários, seja por meio de um computador ou engenharia social. O Red Team continua executando campanhas até que os objetivos sejam alcançados ou o tempo alocado expire.

Nossos exercícios de Red Team são personalizados. Por isso, utilizamos uma metodologia flexível para obter melhores resultados e nos permitir simular com precisão um adversário. Consideramos frameworks padrão da indústria, como CORIE, TIBER e Mitre ATT\&CK, mas não os seguimos rigidamente em favor da flexibilidade.

## Workshop de Modelagem de Ameaças

Antes de iniciar quaisquer campanhas, a Vantico conduzirá um workshop de modelagem de ameaças com as partes interessadas chave para responder às seguintes perguntas:

* Quem provavelmente atacará a organização?
* Quais objetivos os adversários provavelmente terão?
* Que nível de recursos esses adversários possuem?
* Quanto tempo esses adversários persistirão em alcançar seu objetivo?

Essas perguntas são discutidas e o tipo de adversário a ser simulado é estabelecido. Por exemplo, isso pode ser uma ameaça interna ou um atacante oportunista. Em segundo lugar, os seguintes itens são discutidos e acordados:

* Qual é o objetivo principal do Red Team?
* Quais são os objetivos secundários (se houver)?
* Quanto tempo o Red Team durará?
* Quem é o contato principal na organização-alvo?
* Qual é o processo de comunicação entre o Red Team e os contatos dentro da organização-alvo?
* Existem restrições para o Red Team? (Por exemplo, sem intrusão física)
* O Red Team deve acionar a resposta a incidentes de propósito após alcançar seus objetivos?

O objetivo principal é uma ameaça a nível de negócios, em vez de um objetivo técnico. Por exemplo, um objetivo principal poderia ser "roubar o código-fonte" do produto principal da organização.

Objetivos secundários podem ser de nível empresarial ou técnico. Por exemplo, "impedir o acesso legítimo aos registros médicos" ou "obter privilégio de Administrador de Domínio".

Opcionalmente, o Red Team pode receber cartas de ameaça para jogar. Uma carta de ameaça pode ser usada pelo Red Team para desencadear um evento na organização. Por exemplo, uma carta de ameaça pode ser "executar malware na estação de trabalho de um usuário" ou "conectar um implante à rede interna". As cartas de ameaça são úteis quando há restrições para o Red Team, para avançar a narrativa quando o Red Team não consegue progredir em direção ao seu objetivo, ou para simular melhor uma ameaça interna.

## Reconhecimento

O Red Team realizará reconhecimento e coleta de informações sobre a organização-alvo utilizando fontes de Inteligência de Código Aberto (OSINT) e varredura ativa. Para permanecer despercebido, o Red Team aprenderá o máximo possível sobre a organização, seus funcionários e suas práticas comerciais.

Será coletada uma lista de controles de segurança e produtos potencialmente usados pela organização-alvo. Se possível, o Red Team criará um ambiente de laboratório com as mesmas ou semelhantes ferramentas para testar malware personalizado antes de usá-los no campo.

Se uma ameaça interna estiver sendo simulada, o Red Team solicitará acesso a informações que o adversário provavelmente saberia.

## Campanhas

As ações tentadas pelo Red Team enquanto progridem em direção ao seu objetivo principal são divididas em campanhas. Os detalhes de cada campanha dependerão de qual adversário está sendo simulado e qual é o objetivo principal. Por exemplo, uma campanha pode ser "ataque de phishing com drop de malware", "intrusão física" ou "movimentação lateral na rede interna".

O Red Team terá várias campanhas potenciais que podem ser executadas. Essas campanhas são priorizadas de acordo com a probabilidade de avançar os objetivos do Red Team versus a probabilidade de alertar o Blue Team. Os resultados obtidos através de campanhas bem-sucedidas e falhadas são retroalimentados e a prioridade das campanhas pode mudar.

## Preparação

Antes de executar uma campanha, o Red Team reúne o máximo de informações auxiliares possível para aumentar suas chances de sucesso. Malware personalizado é desenvolvido, dispositivos são criados e infraestrutura é montada para auxiliar o Red Team. Um pretexto é criado para justificar a existência dessa campanha. Por exemplo, pode ser "um colega compartilhando um arquivo" ou "uma inspeção do sistema HVAC no escritório".

As campanhas, bem como quaisquer ferramentas e dispositivos, são testados offline contra os controles de segurança presentes na organização-alvo para evitar detecção. A campanha prossegue se a detecção for improvável ou se a detecção não tiver um efeito adverso no Red Team.

## Execução

A campanha é executada e potencialmente ajustada em tempo real para evitar detecção. Se bem-sucedida, o Red Team tentará manter seu nível de acesso recém-obtido e utilizá-lo em campanhas futuras.

Se a campanha falhar, as razões são retroalimentadas para campanhas futuras e o Red Team pode optar por repetir a campanha ou passar para uma nova. Uma campanha falhada pode ter acionado um alerta para o Blue Team e pode fazer com que o Red Team destrua sua infraestrutura atual e reconstrua. A execução de mais campanhas também pode ser interrompida por um tempo para permitir que a tensão diminua.

O Red Team continuará executando campanhas até que os objetivos sejam alcançados ou o prazo alocado expire.

## Acionar Resposta a Incidentes

Um dos objetivos de um exercício de Red Team pode ser testar a capacidade de resposta a incidentes e forense do Blue Team em um cenário simulado do qual eles não estão cientes. Se for esse o caso, e o Red Team tiver alcançado seus objetivos, uma campanha será executada especificamente para chamar a atenção do Blue Team. O Red Team monitorará as ações do Blue Team e verificará se eles são removidos da rede e se os implantes são limpos.

## Debriefing Red/Blue

Após a conclusão de todas as campanhas, a Vantico realizará um debriefing com o Red Team, Blue Team e as partes interessadas chave. Todo o exercício de Red Team será discutido a partir das perspectivas de ambas as equipes para obter insights sobre o que cada equipe observou. Isso ajuda ambas as equipes a aprender e aprimorar suas habilidades, protegendo, em última análise, a organização contra ameaças do mundo real.
