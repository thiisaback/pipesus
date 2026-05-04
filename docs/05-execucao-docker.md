# Executando a ingestão via Docker Compose
   
1. Certifique-se de que o Docker está em execução na sua máquina. Para isso, utilize o seguinte comando no terminal.

    **Linux/macOS/WSL**
    ```bash
    docker --version && docker compose version
    ```

2. Na pasta raiz do projeto (onde está o arquivo `docker-compose.yml`), construa e inicie o container com o seguinte comando.

    **Linux/macOS/WSL**
    ```bash
    docker compose up --build
    ```

3. Aguarde o script concluir o processo de ingestão dos dados do servidor FTP do DataSUS e realizar o upload para o seu bucket na AWS. 
   
4. Para validação do processo, acesse o console da AWS, vá até o serviço **S3** e verifique se os arquivos `.dbc` foram carregados corretamente para a camada bronze do seu bucket.

5. Para encerrar o container e limpar os recursos após a execução, utilize o seguinte comando.

    **Linux/macOS/WSL**
    ```bash
    docker compose down
    ```

---

> [< Anterior - Configurando as variáveis de ambiente](docs/04-config-env.md)