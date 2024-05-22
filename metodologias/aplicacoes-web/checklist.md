---
description: >-
  O serviço da web é o serviço mais comum e extenso e existem vários tipos
  diferentes de vulnerabilidades.
---

# Checklist

**Porta Padrão:** 80 (HTTP), 443 (HTTPS)



<pre><code><strong>PORT     STATE    SERVICE
</strong>80/tcp   open     http
443/tcp  open     ssl/https
</code></pre>

```
nc -v (domínio.com) 80 #GET / HTTP/1.0
openssl s_client -connect (domínio.com)
```
