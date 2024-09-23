# Revisão de código seguro

Revise os detalhes e a metodologia para uma revisão de código seguro.



Uma revisão de código seguro é o exame conduzido por humanos do código-fonte do software para identificar vulnerabilidades de segurança que são o resultado de falhas de design, mas comprovadamente são problemas de segurança válidos. É uma parte importante do ciclo de vida de desenvolvimento de software (SDLC) de qualquer organização e ajuda a melhorar a qualidade geral e a segurança do software e a postura geral de segurança de uma organização.

As revisões de código seguro são um tipo especializado de engajamento que não está incluído em nossa oferta padrão de teste de penetração como serviço (PtaaS). Este serviço é fornecido por nossa equipe de serviços de segurança cibernética.



| Recurso                         | Descrição                                                                                                                                        |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Cumprido por                    | Serviços de Cibersegurança                                                                                                                       |
| Números de créditos             | A partir de 8 créditos\*, mínimo de 4 dias de trabalho                                                                                           |
| Números de testes               | A depender do escopo                                                                                                                             |
| Reteste                         | Sim                                                                                                                                              |
| Data de início mais cedo        | A data de início mais cedo será baseada na disponibilidade. Datas de início típicas de 3 a 5 datas úteis após o teste ser enviado para In Review |
| Duração do teste                | Normalmente entre 8 e 20 dias, dependendo do escopo. A duração exata será finalizada assim que for movido para Planejado.                        |
| Data de vencimento do relatório | 5 dias úteis após a data de término do teste. O relatório será entregue como PDF na seção Relatório da plataforma                                |



**Detalhes da Metodologia**

Na Vantico, seguimos as Diretrizes de Codificação Segura da OWASP quando se trata de Revisão Segura de Código. A Revisão Segura de Código da Cobalt é um exame sistemático do código-fonte. Durante a revisão segura de código, a Cobalt levará em consideração o risco que o código apresenta, o propósito e o contexto do código, a contagem de linhas de código e a(s) linguagem(s) de programação usada(s).

Aqui estão algumas etapas que podem ser incluídas em uma revisão segura de código:

* Analise a composição do software: Inventário de componentes de código aberto e sinalize problemas potenciais usando ferramentas de análise de composição de software (SCA).&#x20;
* Execute Testes de Segurança de Aplicativos Estáticos: Execute uma ferramenta SAST automatizada para identificar vulnerabilidades comuns.&#x20;
* Valide manualmente as descobertas automatizadas: Revise e avalie os resultados automatizados para identificar e validar problemas reais dentro da funcionalidade crítica. Observação: algumas classes de descoberta - como injeção de código - não podem ser validadas sem o envolvimento ativo do aplicativo em execução.&#x20;
* Revise manualmente a lógica de negócios.&#x20;
* Forneça recomendações sobre mitigações razoáveis ​​que possam abordar problemas descobertos ou alterações de código sugeridas ou caminhos de atualização para corrigir descobertas (quando aplicável).

> Nota:
>
> As ferramentas que nossos pentesters usam durante cada fase podem variar de teste para teste.



**Análise da Composição do Software**

Durante a Análise de Composição de Software (SCA), a Vantico analisa componentes de código aberto e de terceiros para vulnerabilidades conhecidas.

As seis fases para SCA são:

* Identificação de Componentes&#x20;
* Detecção de Vulnerabilidade&#x20;
* Conformidade de Licença&#x20;
* Análise de Versão&#x20;
* Avaliação de Risco&#x20;
* Orientação de Remediação

> Ferramentas:
>
> * Semgrep Pro
> * OWASP Dependency-Check
> * Snyk Open Source
> * Trivy
> * Sonatype
> * Jfrog Xray





