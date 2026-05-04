# Criando o usuário IAM para o projeto na AWS

1. Acesse o serviço `IAM` da AWS.

![Imagem Serviço IAM](docs/images/01-01-servico-iam.png)

2. No bloco `Gerenciamento de Acesso` (*Access Management*), selecione o módulo `Usuários` (*IAM users*).

![Imagem Menu Usuários](docs/images/02-02-menu-usuarios.png)

3. Clique na opção `Criar usuário` (*Create user*).

![Imagem Botão Criar Usuário](docs/images/02-03-criar-usuario.png)

4. Crie um `Nome do Usuário` (*User name*) e clique em `Próximo` (*Next*).

![Imagem Botão Criar Usuário](docs/images/02-04-nome-usuario.png)

5. No bloco `Opções de Permissão` (*Permissions options*), clique em `Anexar políticas diretamente` (*Attach policies directly*). Em seguida, no bloco `Políticas de permissões` (*Permissions policies*), pesquise pelo nome da política criada anteriormente e selecione-a. Clique em `Próximo` (*Next*).

*Caso não tenha criado a política na AWS, acesse o tutorial [Configurando a Política na AWS](docs/01-config-aws-politica.md).*

![Imagem Definir Política](docs/images/02-05-definir-politica.png)

6. Revise as informações de criação e clique em `Criar usuário` (*Create user*).

![Imagem Criar Usuário](docs/images/02-06-criar-usuario.png)

---

> [Próximo  - Criando chaves de acesso na AWS >](docs/03-key-aws.md)

> [< Anterior  - Configurando a Política na AWS](docs/01-config-aws-politica.md)