# Low Hanging Fruit

**Checklist Testes Iniciais**

* [x] Ausência de Header
* [x] Js.map
* [x] Integrity
* [ ] SSL/TLS
* [ ] Vulnerabilidade da Versão do Server



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

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Figura: Frontend divido em diretórios</p></figcaption></figure>

Assim iremos ver de forma mais simples e organizada toda a estrutura frontend da aplicação e podemos examinar diversas coisas, como: se possui comentários do Dev sobre sonhas, API,  o que aquilo faz e entender melhor sobre a estrutura.



***

> **Integrity**

Quando uma aplicação Web é desenvolvida, aparece um muitas partes o elemento \<script> ou \<link> em que eles linkam documentos de outras sites  para aquela página específica. Porém através disso há um risco de que o atacante ganhe controle injetando conteúdo maliciosos nos arquivos, com o uso da Integrity estamos mitigando este risco, adiciona mais uma camada de proteção, em que basicamente declaramos este código com criptografia, sendo sha256, sha384 ou sha 512.





***

> **Medidas de anti-adulteração de bibliotecas Javascript não estão em uso**&#x20;

**Descrição:**

Descrição da integridade do **Sub-recurso** Medidas de detecção de adulteração, como _Subresource Integrity (SRI)_, podem identificar quando um arquivo JavaScript externo importado por um aplicativo foi adulterado por **terceiros mal-intencionados.**

Se não forem obtidos de forma segura, esses arquivos podem ser modificados por invasores para obter **controle** sobre a funcionalidade do arquivo e, portanto, **executar código malicioso** no navegador do usuário usando os privilégios de um site válido.

Vários hackers de roubo de informações de alto nível (em particular contra a British Airways) exploraram esse problema de forma muito eficaz para comprometer **informações confidenciais dos clientes.**

**Então**, procure referências a javascript que não tenha a flag.

```
integrity="sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho
1wx4JwY8wC"
```

***

