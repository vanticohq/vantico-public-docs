---
hidden: true
---

# Low Hanging Fruits (primeiro)

Primeiro devemos separar os tipos de serviços que podem ser vulneráveis como SSH, SNMP, SMB, SQL, NFS, FTP, Impressoras, VNC, RDP, Web, Telnet.



### **SMB**

**Checks principais**

* Versão (vulnerabilidades conhecidas)
* SMBv1 habilitado
* MS17-010 (EternalBlue)
* Assinatura SMB desabilitada
* Sessão “guest” habilitada
* Responder / Relay (NTLM Relay)
* Enumeração de shares, usuários e grupos

**Ferramentas**

* Responder (para capturar hashes NTLM, LLMNR)
* Impacket (ntlmrelayx, smbrelay)
* Netexec(para test bruteforce, netexec, enum, Pass the Hash)
* enum4linux (enumeração de shares, usuários, grupos)
* smbclient (listar e acessar shares)
* BloodHound (análise de ambiente AD via shares/dump)

***

### **SNMP**

**Checks principais**

* Comunidades padrão (“public”, “private” etc.)
* Comunidades adivinháveis (nomes de empresa, rede, etc.)
* Versão do SNMP (v1, v2, v3 — criptografia habilitada ou não)
* Acesso de leitura/escrita via comunidade (Write Community)

**Ferramentas**

* onesixtyone (bruteforce de comunidades)
* snmpwalk (coleta de informações, MIBs)
* nmap (scripts snmp-\*)

***

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

### **Impressoras**

**Checks principais**

* Login padrão do fabricante (HP, Xerox, Canon, etc.)
* Interfaces de administração expostas (sem HTTPS ou sem senha)
* Versão/firmware vulneráveis

**Ferramentas**

* nmap (scripts snmp-\* ou porta TCP/UDP específica)
* Acesso web (painel de gerenciamento via portas 80/443)
* Ferramentas específicas do fabricante, se houver

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

### **VNC**

**Checks principais**

* Versão (RealVNC, UltraVNC, TightVNC etc.)
* Login padrão ou sem senha
* Brute force

**Ferramentas**

* nmap (scripts vnc-\*)
* hydra, medusa (força bruta de VNC)

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

* nmap (scripts `http-*`), nikto, whatweb
* wpscan (para WordPress), droopescan (Joomla, Drupal, SilverStripe)
* Burp Suite, WFuzz

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
