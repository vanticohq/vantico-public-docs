# Low Hanging Fruit

***

> Ausência de Headers

Toda vulnerabilidade que envolve a **ausência de cabeçalhos ("header")** deve ser adicionada **separadamente** para cada cabeçalho ausente presente no escopo.



Exemplo de como deve ser evidenciado a Ausência do Header:

<figure><img src="../../.gitbook/assets/Captura de tela 2024-06-13 133028.png" alt=""><figcaption><p>Figura: Request Burp Suite</p></figcaption></figure>



<figure><img src="../../.gitbook/assets/Captura de tela 2024-06-13 132925.png" alt=""><figcaption><p>Figura: Response Burp Suite indicando a ausência do header</p></figcaption></figure>



Por **padrão** os Headers são reportados pelas seguintes severidades:

<figure><img src="../../.gitbook/assets/WhatsApp Image 2024-06-12 at 20.34.08.jpeg" alt=""><figcaption><p>Figura: Severidade de cada cabeçalho</p></figcaption></figure>



Isto é apenas uma **indicação**, porém a severidade de cada cabeçalho deve ser indicado mediante o **impacto** que ele traz ao ambiente testado.



***

> Medidas de anti-adulteração de bibliotecas Javascript não estão em uso

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

