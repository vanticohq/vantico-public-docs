# Low Hanging Fruit

Medidas de anti-adulteração de bibliotecas Javascript não estão em uso



**Descrição:**

Descrição da integridade do **Sub-recurso** Medidas de detecção de adulteração, como _Subresource Integrity (SRI)_, podem identificar quando um arquivo JavaScript externo importado por um aplicativo foi adulterado por **terceiros mal-intencionados.**

Se não forem obtidos de forma segura, esses arquivos podem ser modificados por invasores para obter **controle** sobre a funcionalidade do arquivo e, portanto, **executar código malicioso** no navegador do usuário usando os privilégios de um site válido.

Vários hackers de roubo de informações de alto nível (em particular contra a British Airways) exploraram esse problema de forma muito eficaz para comprometer **informações confidenciais dos clientes.**



**Recomendação:**

Para evitar esta classe de ataques, siga os seguintes passos:

* Use a integridade de sub-recursos (SRI) para verificar recursos de terceiros
* O SRI permite que o navegador verifique o _hash_ criptográfico do recurso baixado em relação a um valor de hash válido e conhecido e bloqueia a execução do script se houver uma exceção:

```
<script src="https://example.com/example-framework.js"
        integrity="sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho
1wx4JwY8wC"
        crossorigin="anonymous"></script>
```

Pode haver casos em que não seja possível calcular hashes de integridade de sub-recursos, pois o conteúdo do arquivo JavaScript é **dinâmico**. Nestes casos, é recomendável entrar em contato com o fornecedor do roteiro ou aceitar o risco.

Para obter detalhes completos sobre a implementação do SRI, consulte os _links_ abaixo.
