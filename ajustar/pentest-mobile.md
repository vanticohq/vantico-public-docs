# Pentest mobile

Testes móveis são um verdadeiro desafio. Esperamos que este guia o ajude a começar.

## Dispositivos Físicos vs Virtuais

Como regra geral, é aconselhável testar em um dispositivo físico. Embora os emuladores Android geralmente sejam bons, eles não representam 100% um dispositivo físico (pense em scanners de impressão digital/reconhecimento facial). Este guia não cobre a configuração de um dispositivo virtual (ainda).

## Jailbreaking/Rooting

A primeira coisa que precisamos fazer é fazer jailbreak/root no dispositivo de teste, se ainda não foi feito. Isso permitirá que você teste o aplicativo de forma mais eficaz.

**iOS**

**Instalar checkra1n**

O checkra1n é um dos exploits de jailbreak mais consistentes, mas esteja ciente de que ele não persiste após reinicializações. Cada vez que for necessária a execução de root, o dispositivo precisará ser reiniciado e re-explorado com o checkra1n.

Atualmente, o checkra1n só suporta execução em Linux e macOS. Há uma iniciativa para criar uma interface gráfica para Windows, mas o progresso está lento. Até lá, se o seu host não for Linux, você deve usar a sua distribuição favorita de Linux live-boot e baixar o checkra1n do site oficial.

Uma vez que seu dispositivo iOS esteja conectado e o checkra1n esteja em execução, o processo é muito simples. Siga os prompts no checkra1n (ele lhe dirá tudo o que você precisa saber) e você deverá ter um iPhone com root funcionando rapidamente.

Após o nosso iPhone estar com root e ligado, você pode acessar um console root conectando-se diretamente via SSH no telefone com as credenciais root/alpine.

**Instalar o servidor Frida**

Para instalar o Frida, precisamos adicionar o repositório [https://build.frida.re](https://build.frida.re/) ao Cydia. Para fazer isso, basta abrir o Cydia, clicar na aba **Sources**, clicar em **Edit** no canto superior direito e depois em **Add** no canto superior esquerdo. Uma vez adicionado, instale o pacote Frida. O Frida deve iniciar automaticamente.

**Android**

No seu computador de teste, instale o `adb` e `fastboot` das ferramentas SDK da plataforma Android, se ainda não estiverem instalados:

**Ubuntu:**

```bash
$ apt install android-tools-adb android-tools-fastboot
```

**Arch:**

```bash
$ pacman -S android-tools
```

**Windows:**

Baixe a versão mais recente das SDK Platform-tools [aqui](https://developer.android.com/studio/releases/platform-tools).

**Habilitar opções de desenvolvedor**

Para acessar o telefone via USB e iniciar o processo de rooting, você precisará habilitar as opções de desenvolvedor e ativar a depuração USB.

1. Em **Configurações > Sobre o telefone**, role para baixo até **Número da versão** (alternativamente, pode ser **Versão do Kernel**) e toque sete vezes até aparecer uma notificação dizendo que as opções de desenvolvedor foram desbloqueadas.
2. Em **Configurações > Opções de desenvolvedor**, habilite a **Depuração USB**. Clique em **OK** no prompt e novamente em **OK** se aparecer outro prompt com uma impressão digital RSA.

Você pode testar se está funcionando corretamente conectando o dispositivo de teste via USB e executando:

```bash
$ adb devices
```

Um número de série deve aparecer, indicando que a depuração USB está funcionando corretamente. Você pode precisar aceitar a impressão digital RSA do computador de teste se o comando falhar.

**Desbloquear o bootloader**

Em **Configurações > Opções de desenvolvedor**, habilite o **Desbloqueio OEM**.

Você pode precisar consultar o fabricante do seu dispositivo de teste para obter mais detalhes sobre o processo de desbloqueio, pois alguns fabricantes têm requisitos diferentes (como a necessidade de um código de desbloqueio).

Geralmente, o processo é o seguinte:

1.  Reinicie no modo fastboot. Você pode fazer isso manualmente pressionando os botões **Power** e **Volume Down** por dez segundos. Caso contrário, você pode simplesmente executar:

    ```bash
    $ adb reboot fastboot
    ```
2.  Desbloqueie o bootloader com uma das seguintes variações:

    ```bash
    $ fastboot oem unlock
    ```

    ```bash
    $ fastboot flashing unlock
    ```

    *   **Para dispositivos Motorola:** Será necessário inserir códigos de desbloqueio no site da Motorola para obter uma chave única.

        ```bash
        $ fastboot oem get_unlock_data
        $ fastboot oem unlock <UNIQUE_KEY>
        ```
    *   **Para dispositivos HTC:** Será necessário inserir um código de desbloqueio no site da HTC para obter um token de desbloqueio único.

        ```bash
        $ fastboot oem get_identifier_token
        $ fastboot oem unlocktoken Unlock_code.bin
        ```

    Você deve receber uma mensagem **OKAY** no seu terminal se for bem-sucedido.
3.  Reinicie o telefone. Faça isso manualmente pelo menu fastboot ou execute:

    ```bash
    $ fastboot reboot
    ```

**Instalar TWRP**

O TWRP (Team Win Recovery Project) é uma recuperação personalizada usada para fazer root no seu dispositivo e substituir o firmware por uma ROM personalizada.

1. Procure seu dispositivo [aqui](https://twrp.me/Devices/) e baixe a versão mais recente do TWRP.
2.  Reinicie seu telefone no bootloader com:

    ```bash
    $ adb reboot bootloader
    ```
3.  Grave a imagem do TWRP no dispositivo:

    ```bash
    $ fastboot flash recovery <NOME_DO_ARQUIVO_TWRP>.img
    ```
4.  Reinicie o dispositivo:

    ```bash
    $ fastboot reboot
    ```
5.  Confirme se o TWRP foi gravado corretamente:

    ```bash
    $ adb reboot recovery
    ```

    Se tudo correu bem, você deverá estar no menu do TWRP.

**Instalar Magisk**

O Magisk é um conjunto de ferramentas poderoso que fornece acesso root e contorna detecções de root e verificações de integridade do sistema.

1. Baixe o arquivo ZIP mais recente do repositório do GitHub para o seu computador de teste.
2.  No TWRP, acesse **Advanced > ADB Sideload** e deslize para iniciar o processo de sideload. Execute:

    ```bash
    $ adb sideload <NOME_DO_ARQUIVO_MAGISK>.zip
    ```
3. Reinicie seu telefone. Se tudo correu bem, você deverá ter o aplicativo Magisk instalado.
4.  Finalmente, você pode verificar se o root está disponível:

    ```bash
    $ adb shell
    $ su
    # ls -l /data/data/
    ```

    Se esses comandos funcionarem, você está pronto para prosseguir.

**Instalar o servidor Frida**

Instalar o servidor Frida diretamente no seu telefone permite a instrumentação dinâmica (hooking em processos para realizar ações interessantes).

1. Descubra a arquitetura do dispositivo.
2. Baixe o servidor Frida mais recente para o seu dispositivo (geralmente `frida-server-VERSÃO-android-ARQUITETURA.xz`).
3.  Descompacte o arquivo:

    ```bash
    $ unxz <NOME_DO_ARQUIVO_FRIDA>.xz
    ```
4.  Envie o arquivo do servidor para o seu dispositivo:

    ```bash
    $ adb root # pode ser necessário
    $ adb push <NOME_DO_ARQUIVO_FRIDA> /data/local/tmp/
    $ adb shell "chmod 755 /data/local/tmp/<NOME_DO_ARQUIVO_FRIDA>"
    $ adb shell "/data/local/tmp/<NOME_DO_ARQUIVO_FRIDA> &"
    ```
5.  Se o Frida estiver instalado no seu computador de teste, teste se o servidor está em execução executando:

    ```bash
    $ frida-ps -U
    ```

    Se você obter uma lista de processos, está tudo certo.

## Configuração

**Ponto de Acesso Sem Fio**

Com um adaptador WiFi USB conectado, use o `create_ap` para criar um ponto de acesso, por exemplo:

```bash
$ create_ap wlan0 eth0 MeuPontoDeAcesso MinhaSenha
```

Isso criará o ponto de acesso **MeuPontoDeAcesso** com a senha **MinhaSenha**. Uma rede sem fio será criada em `wlan0` e NATada através de `eth0`. Basta conectar o telefone ao ponto de acesso e verificar se você pode acessar a Internet.

**Proxy do Burp Suite**

Adicione um novo ouvinte de proxy vinculado ao gateway do ponto de acesso. Se o ponto de acesso foi configurado na sua máquina virtual e você está usando o Burp Suite no seu host, vincule o proxy ao interface host-only/VM NAT.

No dispositivo de teste, configure um proxy nas configurações de rede apontando para o proxy do Burp Suite. Teste se está funcionando tentando acessar [http://burp](http://burp/).

Se for bem-sucedido, baixe o certificado CA e instale-o. [Como instalar um CA personalizado em iPhones](https://support.apple.com/pt-br/guide/iphone/iph3f3ff8aee/ios) e [Como instalar um CA personalizado em Android](https://support.google.com/accounts/answer/6010255?hl=pt-BR).

Após a instalação, verifique se você pode interceptar qualquer coisa enquanto estiver no navegador do dispositivo. Se puder, parabéns! Caso contrário, ou o guia não foi útil ou você perdeu algum passo.

Abra o aplicativo em escopo (se instalado) e verifique se ele funciona corretamente. Se funcionar, parabéns! Você encontrou sua primeira vulnerabilidade! Isso significa que não há pinning de certificado. Se não funcionar, parece que você precisará se esforçar mais e contornar o pinning de certificado.

**Frida**

Se o Frida ainda não estiver instalado, execute:

```bash
$ pip3 install frida-tools
```

**Testar o servidor Frida**

No dispositivo de teste, conecte-se via SSH, localize onde você instalou o servidor Frida e execute-o em segundo plano (se ainda não estiver em execução). Você também pode usar `adb shell` para executá-lo no Android.

No seu computador de teste, verifique se você consegue se conectar ao servidor Frida:

```bash
$ frida-ps -U
```

Se for bem-sucedido, uma lista de processos deve ser exibida.

**Sideloading de Aplicação**

Se você não está testando a versão do aplicativo atualmente disponível na Apple App Store/Google Play Store, precisará fazer o sideloading no dispositivo.

**iPhone**

Para instalar um arquivo IPA (mesmo que não esteja assinado), podemos usar a ferramenta muito útil criada por Karen, o `appinst`. Para obter esta ferramenta, primeiro precisamos adicionar o repositório [https://cydia.akemi.ai/](https://cydia.akemi.ai/) ao Cydia. Para fazer isso, basta abrir o Cydia, clicar na aba **Sources**, clicar em **Edit** no canto superior direito e depois em **Add** no canto superior esquerdo. Depois de feito isso, encontre o pacote **appinst (App Installer)** e instale-o. Agora, a utilidade `appinst` estará disponível para uso a partir da linha de comando. Além disso, para instalar aplicativos móveis assinados incorretamente, você precisará instalar o pacote **AppSync Unified** do mesmo repositório.

Com uma cópia do arquivo IPA do aplicativo no seu computador de teste, execute (as credenciais devem ser `root/alpine`):

```bash
$ scp app-to-install.ipa root@<iphone_ip_address>:~
```

Em seguida, conecte-se via SSH e instale o aplicativo:

```bash
$ ssh root@<iphone_ip_address>
$ appinst app-to-install.ipa
```

**Android**

Com uma cópia do aplicativo APK no seu computador de teste, execute:

```bash
$ adb install <CAMINHO_PARA_APK>
```

Verifique se ele está instalado e abre corretamente!

## Próximos Passos

Agora você pode começar a experimentar ferramentas como:

* **Objection**
* **drozer**
* **r2flutch**
* E mais.

Também recomendamos dar uma olhada nos **Frida Codeshares** para obter alguns exemplos reais de scripts Frida.

## Conclusão

Este guia cobre os passos iniciais para configurar dispositivos móveis para testes de segurança, incluindo o jailbreak/root, configuração de ambientes de teste e uso de ferramentas essenciais. Lembre-se de sempre realizar essas ações de maneira ética e com a devida autorização para evitar consequências legais.
