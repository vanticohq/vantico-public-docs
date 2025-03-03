# Low Hanging Fruits

Primeiro devemos separar os tipos de serviços que podem ser vulneráveis como SSH, SQL, NFS, FTP,  RDP, Web, Telnet.



### **FTP**

**Checks principais**

* FTP Bounce Attack
* Login anônimo habilitado
* Credenciais padrão (ex.: ftp:ftp, anonymous:anonymous)
* Versão do servidor (vulnerabilidades conhecidas)
* Permissão de upload/download em anônimo
* Brute force

**Ferramentas**

* nmap (scripts ftp-\*)
* ftp (cliente para testes manuais)
* hydra, medusa (força bruta)

***

### **SSH**

**Checks principais**

* Versão do OpenSSH (ou outra implementação)
* Métodos de autenticação habilitados (senha, chaves)
* Login root permitido
* Brute force (senhas fracas, chaves privadas vazadas)

**Ferramentas**

* nmap (scripts ssh-\*)
* ssh-audit (verificação da versão, ciphers, etc.)
* hydra, medusa (para brute force)

***

### **NFS**

**Checks principais**

* Shares exportadas (showmount -e \<host>)
* Montagem de shares sem restrição (permissões de leitura/escrita)
* Acesso a arquivos sensíveis (chaves SSH, backups, etc.)

**Ferramentas**

* showmount, rpcinfo
* mount -t nfs
* nmap (scripts nfs-\*)

***

### **MySQL**

**Checks principais**

* Versão do servidor (vulnerabilidades específicas)
* Credenciais padrão ou fracas (root sem senha, etc.)
* Brute force

**Ferramentas**

* nmap (scripts mysql-\*)
* hydra, medusa (força bruta)

***

### **RDP**

**Checks principais**

* Versão RDP (checar vulnerabilidades como BlueKeep – CVE-2019-0708)
* Brute force de credenciais (senhas fracas)

**Ferramentas**

* nmap (scripts rdp-\*)
* rdpscan (ferramenta específica para BlueKeep)
* hydra, medusa (força bruta)

***

### **Web**

**Checks principais**

* Credenciais padrão (admin:admin, root:root, etc.)
* Versão de frameworks (WordPress, Joomla, etc.)
* Falhas conhecidas (SQLi, XSS, RCE, LFI)
* Brute force

**Ferramentas**

* nmap (scripts `http-*`)
* wpscan (para WordPress), droopescan (Joomla, Drupal, SilverStripe)
* Burp Suite, WFuzz&#x20;

***

### **Telnet**

**Checks principais**

* Serviço ainda ativo (obsoleto)
* Credenciais padrão ou fracas
* Brute force

**Ferramentas**

* nmap (scripts telnet-\*)
* telnet (cliente para teste manual)
* hydra, medusa (força bruta)
