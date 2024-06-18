# Low Hanging Fruit

**Checklist Testes Iniciais**

* [x] Ausência de Header
* [x] Js.map
* [x] Integrity
* [x] SSL/TLS
* [x] Vulnerabilidade da Versão do Server
* [x] Portas Abertas
* [x] Nuclei / Katana
* [x] Política de Senhas Permissivas
* [ ] Mensagem de Erros
* [x] Utilizar bibliotecas JavaScript desatualizadas
* [x] Enumeração de Usuário



***

> **Ausência de Headers**

Toda vulnerabilidade que envolve a **ausência de cabeçalhos ("header")** deve ser adicionada **separadamente** para cada cabeçalho ausente presente no escopo.



Exemplo de como deve ser evidenciado a Ausência do Header:

<figure><img src="../../.gitbook/assets/Captura de tela 2024-06-13 133028.png" alt=""><figcaption><p>Figura: Request Burp Suite</p></figcaption></figure>



<figure><img src="../../.gitbook/assets/Captura de tela 2024-06-13 132925.png" alt=""><figcaption><p>Figura: Response Burp Suite indicando a ausência do header</p></figcaption></figure>



Por **padrão** os Headers são reportados pelas seguintes severidades:

<figure><img src="../../.gitbook/assets/WhatsApp Image 2024-06-12 at 20.34.08.jpeg" alt=""><figcaption><p>Figura: Severidade de cada cabeçalho</p></figcaption></figure>



Isto é apenas uma **indicação**, porém a severidade de cada cabeçalho deve ser indicado mediante o **impacto** que ele traz ao ambiente testado.



***

> **Js.map**

É uma ótima forma de investigarmos mais sobre a estrutura do site, através de seu código JavaScript.

Primeiro devemos encontrar o código do bootstrap, basta: Inspecionar Elemento, depois clicamos nos três pontos do  canto superior direito, vamos em "More Tools", "Search", e pesquisamos por "Loading Chunk".

A partir disso iremos procurar no final por "js.map".

Então vamos usar uma ferramenta chamada "unwebpack-sourcemap", através dela usamos o seguinte código como exemplo:

```
python3 unwebpack_sourcemap.py --make-directory 
https://example.com/assets/UserNameComplete-d6c0c7fc8bc309d9b022.js.map 
output
```

Depois de rodar esta ferramenta, iremos visualizar o frontend completo desta maneira:

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption><p>Figura: Frontend divido em diretórios</p></figcaption></figure>

Assim iremos ver de forma mais simples e organizada toda a estrutura frontend da aplicação e podemos examinar diversas coisas, como: se possui comentários do Dev sobre senhas, API,  o que aquilo faz e entender melhor sobre a estrutura.



***

> **Medidas de anti-adulteração de bibliotecas Javascript não estão em uso (Integrity)**

**Descrição:**

Descrição da integridade do **Sub-recurso** Medidas de detecção de adulteração, como _Subresource Integrity (SRI)_, podem identificar quando um arquivo JavaScript externo importado por um aplicativo foi adulterado por **terceiros mal-intencionados.**

Se não forem obtidos de forma segura, esses arquivos podem ser modificados por invasores para obter **controle** sobre a funcionalidade do arquivo e, portanto, **executar código malicioso** no navegador do usuário usando os privilégios de um site válido.

Vários hackers de roubo de informações de alto nível (em particular contra a British Airways) exploraram esse problema de forma muito eficaz para comprometer **informações confidenciais dos clientes.**

**Então**, procure referências a javascript que não tenha a flag.

**Exemplo:**

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption><p>Figura: Exemplo correto com SHA384</p></figcaption></figure>

**Segue o código abaixo:**

```
integrity="sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho
1wx4JwY8wC"
```

***

> **SSL/TLS**

São protocolos de segurança que garantem que a navegação do usuário fique protegida contra um possível vazamento de dados e ataques hackers. Ou seja, toda a informação sensível compartilhada pelo usuário, se mantém criptografada.

Ambos o SSL quanto o TLS, são muito parecidos, porém o TLS é uma versão mais atualizada do SSL.

**TLS:**

**Transport Layer Security**, este protocolo vai codificando toda a mensagem que o usuário envia ao servidor, e são criados chaves de acesso a qual apenas o emissor e receptor tem acesso e quando a informação faz esse caminho, o TLS autentica quem tentou acessar o conteúdo, caso não seja um dos dois, não é possível acessar a mensagem.&#x20;

O protocolo TLS é mais eficaz que o protocolo SSL.



<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Figura: Resultado teste SSL/TLS</p></figcaption></figure>



***

> **Vulnerabilidade da Versão do Server**

Ocorre quando a aplicação divulga informações que podem ajudar um atacante, como a **versão do server** que é utilizada, em que através desta informação, pode-se buscar um exploit para aquela versão e depois utilizar-se deste exploit para fazer a invasão.

Podemos ver no exemplo abaixo, uma aplicação em que divulga a informação da versão do server (nginx 1.18):



<figure><img src="../../.gitbook/assets/Captura de tela 2024-06-17 130915.png" alt=""><figcaption><p>Figura: Exposição da versão do Servidor</p></figcaption></figure>

***

> **Portas Abertas**

Para descobrirmos as portas que estão abertas e quais serviços estão rodando, utilizamos o NMAP.

Nele podemos especificar muitas coisas, como quais portas queremos fazer o teste, Scan UDP, TCP, versão do serviço, tipo de sistema operacional, etc

Para rodarmos um scan simples, usamos:

```
nmap (endereço)
```

Um scan mais completo seria:

```
nmap -Pn -sS -p- (endereço)
```



<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Figura: Resultado scan NMAP</p></figcaption></figure>



***

> **Nuclei / Katana**

**Nuclei:**

Nuclei é usado para enviar requisições entre os alvos baseado em um **template**. Com uma média de 0 falsos positivos, ele possui um **scanning rápido** para um grande número de hosts.



**Exemplo de como utilizar:**

```
nuclei -u (domínio)
```

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Figura: Resultado scan com Nuclei</p></figcaption></figure>



**Katana:**

**Katana** é uma ferramenta rápida e customizável que tem como objetivo realizar **web crawler**, e que possa ser usado de forma ativa ou passiva, utilizando o crawl em múltiplos domínios e subdomínios simultaneamente. Seu objetivo é conseguir informações e endpoints.



**Exemplo de como utilizar:**

```
katana -u (domínio)
```



<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Figura: Resultado scan com Katana</p></figcaption></figure>



***

> **Política de Senhas Permissivas**

Trata-se de quando a aplicação **permite** que o usuário utilize senhas simples e fracas para cadastrar-se, fazendo com que a segurança da aplicação seja mais baixa.

Uma boa política de senhas é aquela em que requer no mínimo 8 caracteres, caracteres especiais, letras maiúsculas e minúsculas... Tornando a senha mais complexa e mais difícil do atacante quebrar.



**Exemplo de uma boa política de senhas:**

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Figura: Requisitos mínimos de senha para cadastro</p></figcaption></figure>



***

> **Mensagem de Erros**

Quando a aplicação retorna um **erro inesperado** assim que um evento acontece, conforme o retorno que a aplicação der em relação ao erro, o atacante pode entender melhor como funciona a estrutura da aplicação, podendo aproveitar-se de alguma vulnerabilidade que pode ser exposta com o erro.

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Figura: Erro de Aplicação</p></figcaption></figure>



***

> **Utilizar bibliotecas JavaScript desatualizadas**

Para encontrar esta vulnerabilidade entramos no código fonte da aplicação, procuramos por arquivos JavaScript, como o **"JQuery"** e sua versão, através desta sua versão um atacante pode buscar por suas vulnerabilidades e explorar uma vulnerabilidade.

**Exemplo:**

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Figura: Versão JQuery no Código Fonte</p></figcaption></figure>



***

> **Enumeração de Usuário**

Ocorre geralmente na área de login, cadastro ou esqueci a senha, em que quando digitamos algum usuário e senha, a aplicação nos retorna que o usuário já existe, ou que o email não está cadastrado, fazendo com que o atacante consiga enumerar quais usuários/emails são válidos ou não.

A mensagem correta que a aplicação deve retornar é de **"Usuário ou Senha Incorretos"** ou **"Caso o email já estiver cadastrado você receberá um link na sua caixa de email"**&#x20;

