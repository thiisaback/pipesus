# Criando chaves de acesso na AWS
      
1. Acesse o serviço `IAM` da AWS.

![Imagem Serviço IAM](docs/images/01-01-servico-iam.png)

2. No bloco `Gerenciamento de Acesso` (*Access Management*), selecione o módulo `Usuários` (*IAM users*).

![Imagem Menu Usuários](docs/images/02-02-menu-usuarios.png)

3. Clique sobre o nome do usuário criado na AWS para a execução do projeto.

*Caso não tenha criado o usuário na AWS, acesse o tutorial [Criando o usuário IAM para o projeto na AWS](docs/02-config-aws-usuario.md).*

![Imagem Selecionar Usuários](docs/images/03-03-selecionar-usuario.png)

4. Selecione a opção `Credenciais de segurança` (*Security credentials*). Em seguida, no bloco `Chaves de acesso` (*Access keys*), clique em `Criar chave de acesso` (*Create access key*).

![Imagem Credenciais de Segurança](docs/images/03-04-credenciais-seguranca.png)

![Imagem Botão Criar Chave de Acesso](docs/images/03-04-botao-criar-chave.png)

5. Selecione o caso de uso mais adequado ao seu contexto de criação da chave de acesso e clique em `Próximo` (*Next*). Para alguns casos, será necessário marcar a caixa de confirmação das recomendações da AWS.

![Imagem Caso de Uso](docs/images/03-05-caso-uso.png)

6. Clique em `Criar chave de acesso` (*Create access key*). Guarde a sua `Chave de acesso` e a `Chave de acesso secreta`, pois elas serão utilizadas para configurar o `.env`.

![Imagem Criar Chave de Acesso](docs/images/03-06-criar-chave.png)

![Imagem Chaves de Acesso](docs/images/03-06-chaves.png)

---

> [< Anterior  - Criando o usuário IAM para o projeto na AWS](docs/02-config-aws-usuario.md)

> [Próximo  - Configurando variáveis de ambiente >](docs/04-config-env.md)