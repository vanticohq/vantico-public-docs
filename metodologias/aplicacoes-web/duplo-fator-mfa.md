# Duplo Fator / MFA

**Verifique se o código enviado para seu e-mail/sms é devidamente atrelado a conta do usuário:**&#x20;

Tente fazer login na conta X usando o código da conta Y.



**Caso em que a aplicação te redireciona para uma página de formulário para que o código de verificação seja preenchido e em seguida te direciona para outra parte da aplicação:**&#x20;

Verifique se o cookie de usuário está sendo settado no momento em que você preenche as credenciais de usuário, isso pode causar com que o atacante pule a etapa de preencher o código 2AF direto para dentro da aplicação.



**Atente-se aos tokens atribuídos a função de "Esqueci minha senha" ou semelhante:**&#x20;

Verifique se o token está sendo devidamente validado alterando o nome/e-mail de usuário e veja como a aplicação se comporta. Você também pode tentar remover o token da solicitação e ver se ele de fato está sendo verificado.



**Cheque quais cookies estão sendo settados no momento em que preenche as credenciais:**&#x20;

Caso exista algum cookie com nome de usuário, indicando que aquele usuário está no processo de 2AF, você pode tentar alterar o valor desse cookie para um valor arbitrário/outra conta e ver como a aplicação se comporta.



**Tente usar o link de verificação recebido no e-mail quando sua conta foi criada:**&#x20;

Você pode tentar reutilizar o link de verificação que foi lhe enviado no e-mail quando sua conta foi criada para verificar se você consegue acessar sua conta sem a necessidade do 2AF.



**Muitas vezes, ao utilizar o link de redefinir senha, após cadastrar uma nova, você é redirecionado diretamente para dentro da sua conta:**&#x20;

Verifique se você consegue usar esse link múltiplas vezes, caso esse comportamento esteja presente, você consiga reutilizar o link e o código atrelado ao link seja previsível, significa que você pode simplesmente roubar outras contas.



**Ainda sobre a função de redefinir senha:**&#x20;

Habilite o 2AF em sua conta, deslogue e utilize a função de redefinir sua senha. Após isso verifique se o 2AF ainda está habilitado, caso contrário, você já sabe.



**Sem rate-limit na tentativa de inserir o código de 2AF:**&#x20;

Nesses casos, tente realizar um brute-force no formulário responsável pelo preenchimento do código que é enviado via e-mail/sms.



**Códigos de backup:**&#x20;

Verifique se é possível realizar brute-force nessa função;&#x20;

Tente os gerar novamente;&#x20;

Verifique se o CORS da página que informa os códigos de backup está devidamente configurado.



**Alterar a senha entre a solicitação e o envio do código de 2AF.**
