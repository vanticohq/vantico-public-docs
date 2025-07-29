# AWS

**Ferramentas:**

Pacu: https://github.com/RhinoSecurityLabs/pacu

ScoutSuite: https://github.com/nccgroup/ScoutSuite

Prowler: https://github.com/prowler-cloud/prowler\


\
**Videos:**&#x20;

Pen test em AWS com o Pacu: [https://www.youtube.com/watch?v=yDf-9LGYJi8\&t=1056s](https://www.youtube.com/watch?v=yDf-9LGYJi8\&t=1056s)

PACU - AWS Exploitation framework by Julio Melo: [https://www.youtube.com/watch?v=6w4m1msB0\_I](https://www.youtube.com/watch?v=6w4m1msB0\_I)

\
**Treinamentos:**

Breaking and Pwning Apps and Servers on AWS and Azure by Appsecco: [https://github.com/appsecco/breaking-and-pwning-apps-and-servers-aws-azure-training/blob/master/documentation/SUMMARY.md](https://github.com/appsecco/breaking-and-pwning-apps-and-servers-aws-azure-training/blob/master/documentation/SUMMARY.md)\


***

PACU\
`run iam__enum_permissions --all-usersrun ec2__enum --instances`\


***

Lista de testes:\
Coletar todos os Ips Públicos e domínios → Fazer port scan para checar por serviços expostos

Enumerar todas as policies associadas a perfis/grupos → Checar por possibilidades de escalação de privilégios

Dumpar todos os registros no Route 53 → Conferir se tem como fazer subdomain takeover em algum\
\


***

Para listar as zonas dentro da conta:

`aws route53 list-hosted-zones`

\
Para ver os domínios dentro de cada zona:\
`aws route53 list-resource-record-sets --hosted-zone-id Z02304912A3UP65CUHNBC | jq -r '.ResourceRecordSets[] | .Name'`\
\
[https://medium.com/@MorattiSec/my-aws-pentest-methodology-14c333b7fb58](https://medium.com/@MorattiSec/my-aws-pentest-methodology-14c333b7fb58)
