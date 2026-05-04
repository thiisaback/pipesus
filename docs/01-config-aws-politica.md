# Configurando a Política na AWS

1. Acesse o serviço `IAM` da AWS.

![Imagem Serviço IAM](docs/images/01-01-servico-iam.png)

2. No bloco `Gerenciamento de Acesso` (*Access Management*), selecione o módulo `Políticas` (*Policies*).

![Imagem Menu Política](docs/images/01-02-menu-politicas.png)

3. Clique na opção `Criar política` (*Create policy*).

![Imagem Criar Política](docs/images/01-03-criar-politica.png)

4. No canto superior direito, selecione a opção `JSON` substitua o código padrão pelo código abaixo. Altere os **dois** textos `NOME_DO_SEU_BUCKET` pelo nome do seu bucket em que os arquivos serão hospedados. Em seguida, clique no botão `Próximo` (*Next*).

   ```json
   {
      "Version": "2012-10-17",
      "Statement": [
         {
               "Sid": "VisualizacaoGlobal",
               "Effect": "Allow",
               "Action": [
                  "s3:ListAllMyBuckets"
               ],
               "Resource": "*"
         },
         {
               "Sid": "GerenciamentoDoBucket",
               "Effect": "Allow",
               "Action": [
                  "s3:CreateBucket",
                  "s3:ListBucket"
               ],
               "Resource": "arn:aws:s3:::NOME_DO_SEU_BUCKET"
         },
         {
               "Sid": "OperacoesComObjetos",
               "Effect": "Allow",
               "Action": [
                  "s3:PutObject",
                  "s3:DeleteObject",
                  "s3:GetObject"
               ],
               "Resource": "arn:aws:s3:::NOME_DO_SEU_BUCKET/*"
         }
      ]
   }
   ```

![Imagem Especificações da Política](docs/images/01-04-especificacoes-politica.png)

5. Defina o `Nome da política` (*Policy name*) e insira uma `Descrição` (*Description*) que facilite a identificação da política. Abaixo temos uma sugestão.
```text
Nome da política: pipeline-cnes-profissionais-politica

Descrição: Politica de autorizacao de servicos para o projeto pipeline-cnes-profissionais.
```

![Imagem Nome da Política](docs/images/01-05-nome-politica.png)

6. Clique em `Criar política` (*Create policy*).
   
![Imagem Criar Política](docs/images/01-06-criar-politica.png)

   ---

> [Próximo  - Criando o usuário IAM para o projeto na AWS >](docs/02-config-aws-usuario.md)