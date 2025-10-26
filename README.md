# desafioAWS_Dio_executando_tarefas_automatizadas_com_dambda_function
Este laboratório tem como objetivo de consolidar meus conhecimentos em tarefas automatizadas com Lambda Function e S3.

# Lambda Function
AWS Lambda é um serviço de computação serverless da Amazon Web Services (AWS) que permite executar código sem precisar provisionar ou gerenciar servidores.

# Amazon S3
Amazon S3 (Simple Storage Service) é um serviço de armazenamento de objetos na nuvem da AWS.

# Amazon DynamoDB
Amazon DynamoDB é um serviço de banco de dados NoSQL (não relacional) da AWS, totalmente gerenciado e serverless.

# IAM
IAM (Identity and Access Management) é o serviço de segurança central da AWS que controla quem pode fazer o quê na sua conta.

# Amazon API Gateway
Amazon API Gateway é um serviço totalmente gerenciado da AWS que atua como a "porta de entrada" para suas aplicações e serviços backend.

# O que foi feito
Foi feita a ilustração de como a arquitetura de um Sistema de Processamento de Notas Fiscais utiliza os serviços da AWS, seguindo o padrão de uma arquitetura serverless (sem servidor).

# Explicação da Arquitetura
O fluxo de trabalho funciona em 4 etapas principais:
Entrada de Dados (Upload do Arquivo):
O Usuário sobe um arquivo (nota fiscal em formato JSON) diretamente para um bucket no Amazon S3.
Acionamento (Trigger):
O Amazon S3, ao detectar o novo arquivo (o trigger), aciona automaticamente a próxima etapa do processo.
Processamento de Dados (AWS Lambda):
Uma AWS Lambda Function (Função Lambda) é invocada (chamada) pelo S3.
A Lambda Function executa o código que:
Lê e valida o arquivo JSON recém-carregado.
Extrai os campos relevantes da nota fiscal (número, cliente, valor, data, etc.).
Grava esses dados extraídos no banco de dados.
Armazenamento e Exposição (DynamoDB e API Gateway):
O Amazon DynamoDB armazena os dados estruturados da nota fiscal.
O Amazon API Gateway (opcional) é utilizado para criar uma API RESTful. Ele permite que outros sistemas ou aplicativos consultem os dados gravados no DynamoDB de forma segura.

# Componentes AWS Utilizados (e suas Funções):
Componente - Função no Sistema
Amazon S3 - Armazenamento de Objetos: Armazena o arquivo JSON bruto da nota fiscal. Serve como ponto de entrada e trigger (gatilho) do processo.
AWS Lambda - "Processamento: Executa o código da lógica de negócios (ler, validar e extrair dados) sem gerenciar servidores."
Amazon DynamoDB - Banco de Dados NoSQL: Armazena de forma rápida e escalável os dados limpos e relevantes que foram extraídos da nota fiscal.
IAM,"Segurança -  Gerencia as permissões de acesso. Por exemplo, define que a Lambda Function tem permissão para ler o S3 e gravar no DynamoDB."
API Gateway - Interface de Acesso (Opcional): Cria um ponto de entrada para consultar os dados do DynamoDB por meio de uma API externa.




