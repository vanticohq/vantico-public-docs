# Movimentação Lateral

O **Putty** é uma ferramenta de emulação de terminal open source, em que suporta diversos protocolos, como: SSH (com tunelamento), Telnet, Serial, Rlogin, etc.&#x20;

Funciona tanto para Windows ou Linux,  se faz fácil de instalação (arquivo .exe), sem custos e possui uma interface bem customizável, possibilitando salvar os hosts para acesso mais rápido.



A ferramenta Putty é muito útil para principalmente tunelamentos via SSH. Mas o que é um tunelamento?



**Tunelamento SSH ou SSH Port Forwarding** é um método para criar uma conexão criptografada (um túnel) entre uma máquina cliente e um servidor permitindo a troca (redirecionamento) das portas de acesso aos serviços.

Esse método é útil para transportar dados de serviços que utilizem protocolos não criptografados, como VNC ou FTP, evitar monitoramento de rede e dar _bypass_ em firewalls.



Como fazer isso com o Putty?



Inicialmente você irá configurá-lo da seguinte maneira:



Em _Session_, você irá adicionar o IP da sua máquina com a porta 22;

Depois clique em + na parte de SSH e vá em _Tunnels_;

Dentro de _Tunnels_, em _Source port_, você irá colocar o seu local host com a porta (ex: 172.0.0.1:1000);

E em _Destination_, o IP que você pretende se conectar com a porta;

Clica em _Open_;

Vai abrir um terminal em que você irá fazer login SSH;

Depois de feito, basta você fazer uma conexão com seu local host, que pode ser feito via _RDP (Remote Desktop Protocol)_ e você já terá concluído seu tunelamento.&#x20;

