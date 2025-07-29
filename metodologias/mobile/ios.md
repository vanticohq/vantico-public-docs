# iOS

## Dispositivos físicos × emuladores

Sempre prefira um iPhone real: recursos como Face ID e Touch ID não são totalmente reproduzidos em VMs/emuladores.

## Jailbreak (checkra1n)

1. Execute o **checkra1n** (Linux/macOS). O jailbreak não é persistente — será necessário reexecutá‑lo após cada reboot.
2. Após o boot com jailbreak, conecte‑se via SSH (`root/alpine`).
3. **Instale o Frida Server** adicionando `https://build.frida.re` ao Cydia → _Sources → Edit → Add_ e instale o pacote _frida_ (inicia automaticamente).

## Configuração de rede & proxy

1.  Crie um AP Wi‑Fi:

    ```bash
    bashCopiarEditarcreate_ap wlan0 eth0 MeuPontoDeAcesso MinhaSenha
    ```
2. No Burp, adicione um _listener_ ligado ao gateway do AP.
3. No iPhone: defina o proxy de rede apontando para o Burp e instale o certificado CA personalizado.

## Frida Tools

_Instalação local:_

```bash
pip3 install frida-tools
frida-ps -U           # lista processos no dispositivo
```

Use scripts próprios ou do **Frida CodeShare** para bypass de SSL‑pinning e jailbreak‑detection.

## Sideloading de apps (.ipa)

1. Adicione o repo `https://cydia.akemi.ai/` no Cydia e instale **AppSync Unified** + **appinst**.
2.  Copie o `.ipa` para o aparelho:

    ```bash
    scp app.ipa root@<ip_iphone>:~
    ssh root@<ip_iphone> "appinst app.ipa"
    ```

#### Próximos passos / Ferramentas úteis

* **r2frida / r2flutch**
* **Burp Suite / OWASP  ZAP**
* **Frida**
