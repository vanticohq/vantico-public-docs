# Low Hanging Fruits - VPN

#### **Múltiplas conexões**

Quando a mesma conta da VPN é usada por mais de uma sessão ao mesmo tempo, como forma de validação, deve ser aberto sessões simultâneas com duas origens diferentes.

Deve validar também quando o logout é realizado se apenas uma das sessões é encerrada ou ambas.

***

#### **MFA**

O MFA deve ser implementado de maneira obrigatória ao usuário, ao fazer a requisição de login na VPN.

***

#### **Restrição por geolocalização**

Para validar essa vulnerabilidade, antes de realizar o login na VPN, deve ser ativado outra VPN levando o IP para outro país a fim de validar a restrição por geolocalização.

***

#### **Enumeração**

A VPN deve apresentar a mesma resposta ao inserir usuários válidos e inválidos em todos os fluxos como no campo de login e redefinição de senha, impedindo com que a vulnerabilidade de enumeração ocorra.

***

#### **Automação**

Algumas ferramentas como _Nuclei_, _ike-scan_ são muito úteis para automatização e check de itens presentes na página da VPN e na VPN em si.

