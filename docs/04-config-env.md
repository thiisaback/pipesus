# Configurando as variáveis de ambiente
   
1. Na pasta `pipeline-cnes-professionals` (clonada do GitHub), faça uma cópia do arquivo `.env.example`, renomeando-a para `.env`. Esse processo poderá ser feito no terminal, a partir do seguinte comando. 

    **Linux/macOS/WSL**
    ```bash
    cp .env.example .env
    ```

    O arquivo `.env` terá a seguinte estrutura.

    ```bash
    # Amazon Web Services (AWS)
    AWS_ACCESS_KEY_ID=SUA_AWS_ACCESS_KEY_ID
    AWS_SECRET_ACCESS_KEY=SUA_AWS_SECRET_ACCESS_KEY
    AWS_DEFAULT_REGION=REGIAO_DO_BUCKET_AWS
    AWS_BUCKET_NAME=NOME_DO_SEU_BUCKET
    ```

2. Insira a chave de acesso gerada na AWS na variável `AWS_ACCESS_KEY_ID` e a chave de acesso secreta na variável `AWS_SECRET_ACCESS_KEY`.

    *Caso não tenha gerado a chave de acesso na AWS, acesse o tutorial [Criando chaves de acesso na AWS](docs/03-key-aws.md).*

3. Insira a região da AWS de criação e manutenção do bucket na variável `AWS_DEFAULT_REGION`. 

    *Confira as regiões disponíveis na seção [**Disponibilidade de regiões**](https://docs.aws.amazon.com/pt_br/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html), coluna **Região** da tabela, no site da AWS.*

4. Insira, na variável `AWS_BUCKET_NAME`, o nome do bucket S3 em que os dados serão armazenados. O nome do bucket deverá ser o mesmo que foi definido no passo 4 da [Configuração da Política](docs/01-config-aws-politica.md) na AWS.

5. Salve o arquivo `.env`.

---

> [< Anterior - Criando chaves de acesso na AWS](docs/03-key-aws.md)

> [Próximo - Executando a ingestão via Docker Compose >](docs/05-execucao-docker.md)