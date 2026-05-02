
# Pipeline de Extração de Dados de Profissionais do CNES

![Status: Em Desenvolvimento](https://img.shields.io/badge/Status-Em%20Desenvolvimento-orange?style=for-the-badge)

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logoColor=white)
![AWS S3](https://img.shields.io/badge/Amazon%20S3-569A31?style=for-the-badge&logo=amazons3&logoColor=white)
![AWS Lambda](https://img.shields.io/badge/AWS%20Lambda-FF9900?style=for-the-badge&logo=awslambda&logoColor=white)
![AWS Glue](https://img.shields.io/badge/AWS%20Glue-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)
![AWS Athena](https://img.shields.io/badge/Amazon%20Athena-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)


## 1. Visão Geral e Valor de Negócio
No setor de saúde brasileiro, a consistência dos dados cadastrais é um pilar crítico de *compliance* governamental e eficiência financeira. O Cadastro Nacional de Estabelecimentos de Saúde (CNES) é o registro oficial do Ministério da Saúde. Divergências entre o sistema interno de Recursos Humanos (RH) de uma instituição de saúde e os registros do CNES — como, por exemplo, um profissional desligado no RH que permanece ativo no portal governamental — podem gerar riscos de auditoria, multas severas e glosas (não pagamento) por parte das operadoras de saúde.

**O Problema:** Em muitas instituições, o cruzamento entre as bases internas (RH) e as públicas (CNES) é um processo manual, extraído via planilhas e altamente suscetível a erros humanos, consumindo dezenas de horas mensais das equipes administrativas.

**A Solução:** Desenvolvimento de uma pipeline de dados escalável na nuvem AWS. O fluxo inicia com **scripts Python** que realizam a extração dos arquivos diretamente do FTP do DataSUS, carregando-os preservados em seu formato original (`.dbc`) na camada **Bronze** do Amazon S3. A conversão para formatos otimizados e a limpeza das informações ocorrem apenas durante a transição para a camada **Silver**, garantindo um histórico bruto e imutável. Esse processamento segue uma **Arquitetura Medallion** orientada a eventos, orquestrada via AWS Lambda e AWS Glue. Por fim, os dados consolidados na camada **Gold** são disponibilizados para consumo analítico via Amazon Athena. A estrutura foi desenhada visando evolução contínua, preparada para a adoção futura do **Apache Airflow** na orquestração da ingestão.

**Impacto e Visão Estratégica:**
* **Automação e Eficiência:** Substituição de extrações manuais por um fluxo programático, eliminando a barreira técnica dos arquivos legados do DataSUS e liberando horas operacionais do time de RH.
* **Governança e *Compliance*:** Criação de uma base de dados estruturada e confiável (*Fonte únida de verdade*) para informações públicas de saúde.
* **Habilitação de Auditorias:** A estrutura disponibilizada no Athena permite integração fluida com ferramentas de BI (Analytics) e execução de scripts de validação cruzada, viabilizando alertas proativos de divergências cadastrais.
---

## 2. Arquitetura do Sistema e Fluxo de Dados

A pipeline foi desenhada utilizando uma **Arquitetura Medallion** orientada a eventos na AWS, garantindo escalabilidade, governança e separação clara das etapas de processamento.

**[IMAGEM DA ARQUITETURA]**

O fluxo de dados (*Data Flow*) ocorre da seguinte maneira:

1. **Fonte de Dados e Ingestão:**
   * Os dados públicos de profissionais do CNES são extraídos diretamente do **DataSUS** (via FTP), originalmente no formato `.dbc` (padrão do SUS).
   * A extração e conversão inicial são realizadas através de **Scripts em Python**, que realizam o *upload* dos arquivos brutos para a nuvem.

2. **Armazenamento e Transformação (AWS Medallion Architecture):**
   * **Camada Bronze (Amazon S3):** Atua como *Landing Zone*, armazenando os dados brutos exatamente como vieram da fonte.
   * **AWS Lambda (Trigger):** Assim que novos arquivos chegam no bucket Bronze, uma função Lambda é acionada automaticamente para iniciar o job de ETL.
   * **AWS Glue (ETL & Orchestration):** Responsável por todo o processamento, limpeza, tipagem e particionamento dos dados, orquestrando a passagem dos dados para as próximas camadas.
   * **Camada Silver (Amazon S3):** Armazena os dados limpos, filtrados e convertidos para Parquet, prontos para cruzamentos.
   * **Camada Gold (Amazon S3):** Contém os dados refinados, agregados e modelados sob a ótica de negócio, prontos para consumo.

3. **Disponibilização:**
   * **Amazon Athena:** Atua como motor de consultas (*Query Engine*) *serverless*, permitindo realizar consultas SQL diretamente nos arquivos da camada Gold.
   * A partir do Athena, os dados ficam disponíveis para conexão com ferramentas de **Analytics/BI** ou para consumo via **Scripts Python** por outras aplicações da instituição.
---
