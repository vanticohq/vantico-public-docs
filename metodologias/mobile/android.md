# Android

## Dispositivos Físicos vs Virtuais&#x20;

Como regra geral, é aconselhável testar em um dispositivo físico. Embora os emuladores Android geralmente sejam bons, eles não representam 100% um dispositivo físico (pense em scanners de impressão digital/reconhecimento facial). Este guia não cobre a configuração de um dispositivo virtual.



## Jailbreaking/Rooting&#x20;

A primeira coisa que precisamos fazer é fazer jailbreak/root no dispositivo de teste, se ainda não foi feito. Isso permitirá que você teste o aplicativo de forma mais eficaz.

### Android&#x20;

No seu computador de teste, instale o adb e fastboot das ferramentas SDK da plataforma Android, se ainda não estiverem instalados:&#x20;

**Ubuntu:**&#x20;

```
$ apt install android-tools-adb android-tools-fastboot
```

**Arch:**&#x20;

```
$ pacman -S android-tools
```

**Windows:**&#x20;

Baixe a versão mais recente das SDK Platform-tools [aqui](https://developer.android.com/studio/releases/platform-tools).&#x20;

#### **Habilitar opções de desenvolvedor**&#x20;

Para acessar o telefone via USB e iniciar o processo de rooting, você precisará habilitar as opções de desenvolvedor e ativar a depuração USB.&#x20;

1. Em **Configurações > Sobre o telefone**, role para baixo até **Número da versão** (alternativamente, pode ser **Versão do Kernel**) e toque sete vezes até aparecer uma notificação dizendo que as opções de desenvolvedor foram desbloqueadas.&#x20;
2. Em **Configurações > Opções de desenvolvedor**, habilite a **Depuração USB.** Clique em **OK** no prompt e novamente em **OK** se aparecer outro prompt com uma impressão digital RSA.&#x20;

Você pode testar se está funcionando corretamente conectando o dispositivo de teste via USB e executando:

```
$ adb devices
```

Um número de série deve aparecer, indicando que a depuração USB está funcionando corretamente. Você pode precisar aceitar a impressão digital RSA do computador de teste se o comando falhar.

**Desbloquear o bootloader**&#x20;

Em **Configurações > Opções de desenvolvedor**, habilite o **Desbloqueio OEM**.&#x20;

Você pode precisar consultar o fabricante do seu dispositivo de teste para obter mais detalhes sobre o processo de desbloqueio, pois alguns fabricantes têm requisitos diferentes (como a necessidade de um código de desbloqueio).&#x20;

Geralmente, o processo é o seguinte:&#x20;

1. Reinicie no modo fastboot. Você pode fazer isso manualmente pressionando os botões **Power** e **Volume Down** por dez segundos. Caso contrário, você pode simplesmente executar:&#x20;

<pre><code><strong>$ adb reboot fastboot
</strong></code></pre>

2. Desbloqueie o bootloader com uma das seguintes variações:&#x20;

```
$ fastboot oem unlock
```

```
$ fastboot flashing unlock
```

* **Para dispositivos Motorola**: Será necessário inserir códigos de desbloqueio no site da Motorola para obter uma chave única.&#x20;

```
$ fastboot oem get_unlock_data 
$ fastboot oem unlock <UNIQUE_KEY>
```

* Para dispositivos HTC: Será necessário inserir um código de desbloqueio no site da HTC para obter um token de desbloqueio único.&#x20;

```
$ fastboot oem get_identifier_token 
$ fastboot oem unlocktoken Unlock_code.bin
```

Você deve receber uma mensagem **OKAY** no seu terminal se for bem-sucedido.&#x20;

3. Reinicie o telefone. Faça isso manualmente pelo menu fastboot ou execute:&#x20;

```
$ fastboot reboot
```

**Instalar TWRP**&#x20;

O TWRP (Team Win Recovery Project) é uma recuperação personalizada usada para fazer root no seu dispositivo e substituir o firmware por uma ROM personalizada.&#x20;

1. Procure seu dispositivo [aqui ](https://twrp.me/Devices/)e baixe a versão mais recente do TWRP.&#x20;
2. Reinicie seu telefone no bootloader com:&#x20;

```
$ adb reboot bootloader
```

3. Grave a imagem do TWRP no dispositivo:&#x20;

```
$ fastboot flash recovery <NOME_DO_ARQUIVO_TWRP>.img
```

4. Reinicie o dispositivo:&#x20;

```
$ fastboot reboot
```

5. Confirme se o TWRP foi gravado corretamente:&#x20;

```
$ adb reboot recovery
```

Se tudo correu bem, você deverá estar no menu do TWRP.

**Instalar Magisk**&#x20;

O Magisk é um conjunto de ferramentas poderoso que fornece acesso root e contorna detecções de root e verificações de integridade do sistema.&#x20;

Baixe o arquivo ZIP mais recente do repositório do GitHub para o seu computador de teste.&#x20;

No TWRP, acesse **Advanced > ADB Sideload** e deslize para iniciar o processo de sideload.&#x20;

Execute:&#x20;

```
$ adb sideload <NOME_DO_ARQUIVO_MAGISK>.zip 
```

Reinicie seu telefone. Se tudo correu bem, você deverá ter o aplicativo Magisk instalado.&#x20;

Finalmente, você pode verificar se o root está disponível:&#x20;

```
$ adb shell 
$ su
# ls -l /data/data/
```

Se esses comandos funcionarem, você está pronto para prosseguir.

**Instalar o servidor Frida**&#x20;

Instalar o servidor Frida diretamente no seu telefone permite a instrumentação dinâmica (hooking em processos para realizar ações interessantes).&#x20;

Descubra a arquitetura do dispositivo.&#x20;

Baixe o servidor Frida mais recente para o seu dispositivo (geralmente `frida-server-VERSÃO-android-ARQUITETURA.xz)`.&#x20;

Descompacte o arquivo: &#x20;

```
$ unxz <NOME_DO_ARQUIVO_FRIDA>.xz
```

Envie o arquivo do servidor para o seu dispositivo:&#x20;

```
$ adb root # pode ser necessário 
$ adb push <NOME_DO_ARQUIVO_FRIDA> /data/local/tmp/ 
$ adb shell "chmod 755 /data/local/tmp/<NOME_DO_ARQUIVO_FRIDA>" 
$ adb shell "/data/local/tmp/<NOME_DO_ARQUIVO_FRIDA> &" 
```

Se o Frida estiver instalado no seu computador de teste, teste se o servidor está em execução executando:&#x20;

```
$ frida-ps -U
```

Se você obter uma lista de processos, está tudo certo.



## Configuração&#x20;

**Ponto de Acesso Sem Fio**&#x20;

Com um adaptador WiFi USB conectado, use o create\_ap para criar um ponto de acesso, por exemplo:&#x20;

```
$ create_ap wlan0 eth0 MeuPontoDeAcesso MinhaSenha 
```

Isso criará o ponto de acesso **MeuPontoDeAcesso** com a senha **MinhaSenha**. Uma rede sem fio será criada em `wlan0` e NATada através de `eth0`. Basta conectar o telefone ao ponto de acesso e verificar se você pode acessar a Internet.

**Proxy do Burp Suite**&#x20;

Adicione um novo ouvinte de proxy vinculado ao gateway do ponto de acesso. Se o ponto de acesso foi configurado na sua máquina virtual e você está usando o Burp Suite no seu host, vincule o proxy ao interface host-only/VM NAT.&#x20;

No dispositivo de teste, configure um proxy nas configurações de rede apontando para o proxy do Burp Suite. Teste se está funcionando tentando acessar http://burp.&#x20;

Se for bem-sucedido, baixe o certificado CA e instale-o. [Como instalar um CA personalizado em iPhones](https://support.apple.com/pt-br/guide/iphone/iph3f3ff8aee/ios) e [Como instalar um CA personalizado em Android](https://support.google.com/accounts/answer/6010255?hl=pt-BR).&#x20;

Após a instalação, verifique se você pode interceptar qualquer coisa enquanto estiver no navegador do dispositivo. Se puder, parabéns! Caso contrário, ou o guia não foi útil ou você perdeu algum passo.&#x20;

Abra o aplicativo em escopo (se instalado) e verifique se ele funciona corretamente. Se funcionar, parabéns! Você encontrou sua primeira vulnerabilidade! Isso significa que não há pinning de certificado. Se não funcionar, parece que você precisará se esforçar mais e contornar o pinning de certificado.

**Frida**&#x20;

Se o Frida ainda não estiver instalado, execute:&#x20;

```
$ pip3 install frida-tools 
```

**Testar o servidor Frida**&#x20;

No dispositivo de teste, conecte-se via SSH, localize onde você instalou o servidor Frida e execute-o em segundo plano (se ainda não estiver em execução). Você também pode usar adb shell para executá-lo no Android.&#x20;

No seu computador de teste, verifique se você consegue se conectar ao servidor Frida:&#x20;

```
$ frida-ps -U 
```

Se for bem-sucedido, uma lista de processos deve ser exibida.&#x20;



## **Sideloading de Aplicação**&#x20;

Se você não está testando a versão do aplicativo atualmente disponível na Apple App Store/Google Play Store, precisará fazer o sideloading no dispositivo.

**Android**&#x20;

Com uma cópia do aplicativo APK no seu computador de teste, execute:&#x20;

```
$ adb install <CAMINHO_PARA_APK> 
```

Verifique se ele está instalado e abre corretamente!
