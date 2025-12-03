# Low Hanging Fruits

> **MFA na VPN**

O MFA deve ser implementado de maneira obrigatória ao usuário, ao fazer a requisição de login na VPN.



***

> **Proteção por geolocalização na VPN**

Para validar essa vulnerabilidade, antes de realizar o login na VPN, deve ser ativado outra VPN levando o IP para outro país a fim de validar a restrição por geolocalização.



***

> **Múltiplas conexões na VPN**

Quando a mesma conta da VPN é usada por mais de uma sessão ao mesmo tempo, como forma de validação, deve ser aberto sessões simultâneas com duas origens diferentes.

Deve validar também quando o logout é realizado se apenas uma das sessões é encerrada ou ambas.



***

> **LDAP bind anônimo**

Validar se o LDAP permite bind anônimo, pode se usar o comando a seguir.

```
ldapsearch -x -H ldap://{IP} -b "<baseDN>"
```



***

> **Assinatura LDAP**

Validar se o LDAP utiliza de assinatura.



***

> **SMB com shares abertas para usuários anônimos**

Validar se o SMB permite o acesso anônimo as shares, pode ser utilizando o seguinte comando para validar.

```
nxc smb (alvo) -u 'guest' -p '' --shares
```



***

> **SMBv1**

Validar se o SMBv1 está habilitado na aplicação, o correto é utilizar algoritmos mais fortes e atuais como o SMBv3.



***

> **Assinatura SMB**

Verificar se o SMB utiliza de assinatura.



***

> **SNMP com communitys padrões**

Verificar se o SNMP utiliza de communitys padrões como _private_, _public_.



***

> **Terrapin SSH**

Validar se os serviços de SSH abertos estão vulneráveis a Terrapin.



***

> **FTP com usuário anônimo habilitado**

Deve ser realizado a tentativa de login anônimo no FTP utilizando as seguintes credenciais.

```
anonymous:anonymous
```

```
anonymous:(vazio)
```



***

> **SMTP openrelay**

Verificar se o SMTP não possui login habilitado, o que permite o openrelay.



***

> **Gerenciamento de patch insuficiente**

Deve ser realizado uma busca pelas versões dos serviços a seguir, buscando vulnerabilidades conhecidas ou versões desatualizadas ([https://endoflife.date/](https://endoflife.date/)).

Deve ser validado os seguintes serviços:

* Windows
* Windows Server
* Linux
* Samba
* SSH
* FTP
* Banco de dados
* Outros serviços identificados



***

> **RDP com nla desabilitado**

Identificar se o nla está ativoado no serviço RDP, para isso basta realizar uma busca com o NetExec, o comando a seguir retorna o resultado esperado.

```
nxc rdp (alvo)
```



***

> **Política de senhas fracas**

Verificar se a política de senhas cumpre com no mínimo 8 caracteres, _password history lenght_ com no mínimo 24, _minimium password age_ com o valor ideal de 1.

Para validar isso, pode ser utilizado o NetExec.

```
nxc smb (alvo) -u 'guest' -p '' --pass-pol
```



***

> **Política de senhas sem bloqueio**

Validar se possui a diretiva account lockout threshold definida, para isso podemos executar o seguinte comando.

```
nxc smb (alvo) -u 'guest' -p '' --pass-pol
```



***

> **Senhas padrões**

Deve ser validado após identificar os serviços se os mesmo possuem senhas padrões definidas. Os serviços são:

* Banco de dados
* Web



***

> **Brute force**

Realizar ataques de brute force nos serviços identificados, como:

* FTP
* SSH
* Banco de dados
* RDP

<br>
