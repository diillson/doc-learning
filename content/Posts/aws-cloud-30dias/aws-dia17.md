---
title: "Dia 17: CLI e SDKs"
date: "2024-08-22"
description: "AWS Command Line Interface (CLI) e Software Development Kits (SDKs)."
categories: ["Cloud"]
tags: ["SDK", "aws sdk", "cli", "developement"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia17"]
author: ["Edilson Freitas"]
cover:
  image: images/cli.png
  hiddenInList: true
---

## Bem-vindo ao Dia 17 do nosso curso de 30 dias sobre AWS! 

Hoje, mergulharemos profundamente no universo da AWS Command Line Interface (CLI) e dos Software Development Kits (SDKs).

Essas ferramentas são essenciais para otimizar seus fluxos de trabalho na AWS, permitindo que você automatize tarefas e interaja com os serviços da AWS de maneira programática. Vamos embarcar nesta jornada para aproveitar o poder da AWS CLI e dos SDKs!


### Introdução à AWS Command Line Interface (CLI):

Aqui está uma visão mais detalhada de como começar a usar a AWS CLI:

1. **Instalação:**

   O primeiro passo é instalar a AWS CLI na sua máquina local. A AWS CLI é compatível com sistemas operacionais Windows, macOS e Linux. Veja como você pode instalá-la:

    - **Windows:** Você pode instalar a AWS CLI no Windows usando o instalador MSI. Baixe o instalador na documentação oficial da AWS CLI e siga o assistente de instalação.
    - **macOS:** No macOS, você pode instalar a AWS CLI usando o gerenciador de pacotes Homebrew. Abra uma janela de terminal e execute o comando:

    ```sh
    brew install awscli
    ```

    - **Linux:** A instalação no Linux varia dependendo da sua distribuição. Você pode instalar a AWS CLI usando o gerenciador de pacotes específico da sua distribuição. Por exemplo, no Ubuntu, você pode usar o apt:

    ```sh
    sudo apt-get install awscli
    ```

2. **Configuração:**

   Uma vez que a AWS CLI esteja instalada, você precisa configurá-la com suas credenciais da AWS. Essas credenciais incluem um Access Key ID e um Secret Access Key, que você pode obter no Console de Gerenciamento da AWS. Veja como configurar a AWS CLI:

   Abra um terminal ou prompt de comando e execute o seguinte comando:

    ```sh
    aws configure
    ```

   Você será solicitado a inserir seu Access Key ID, Secret Access Key, região padrão e formato de saída padrão. Após inserir essas informações, a AWS CLI armazenará essas credenciais em um arquivo localizado no seu diretório pessoal ("~/.aws/credentials" no Linux/macOS ou "%UserProfile%\.aws\credentials" no Windows).

3. **Comandos Básicos:**

   Com a AWS CLI configurada, você já pode começar a usá-la para interagir com os serviços da AWS a partir da linha de comando. Aqui estão alguns comandos básicos para você começar:

    - Listar Instâncias EC2:

    ```sh
    aws ec2 describe-instances
    ```

    - Listar Buckets S3:

    ```sh
    aws s3 ls
    ```

    - Criar um Par de Chaves EC2:

    ```sh
    aws ec2 create-key-pair --key-name MyKeyPair
    ```

    - Excluir um Bucket S3:

    ```sh
    aws s3 rb s3://my-bucket-name --force
    ```

4. **Recursos Avançados:**

   A AWS CLI oferece vários recursos avançados para melhorar sua experiência na linha de comando, incluindo:

    - **Formatação de Saída:** Você pode especificar o formato de saída dos comandos da AWS CLI usando a opção `--output`. Os formatos incluem JSON, texto, tabela e outros.
    - **Filtragem:** Use o parâmetro `--query` para filtrar os resultados dos comandos da AWS CLI com base em critérios específicos.
    - **Paginação:** Alguns comandos da AWS CLI retornam resultados paginados. Use o parâmetro `--page-size` para controlar o número de itens por página e o parâmetro `--starting-token` para iniciar a paginação a partir de um token específico.

### Explorando os SDKs da AWS para diferentes linguagens de programação:

1. **Escolhendo o SDK Certo:**

   A AWS oferece SDKs para linguagens de programação populares, incluindo Python, JavaScript (Node.js), Java, .NET (C#), Ruby, Go, PHP, e mais. Escolha o SDK que se alinha com a linguagem de programação e os requisitos do seu projeto.

    - **Python:** Boto3 é o SDK da AWS para Python. Ele fornece um conjunto abrangente de ferramentas para trabalhar com os serviços da AWS em Python.
    - **JavaScript/Node.js:** O SDK da AWS para JavaScript (AWS SDK for Node.js) permite que você construa aplicações usando Node.js e interaja com os serviços da AWS.
    - **Java:** A AWS oferece o AWS SDK para Java, que disponibiliza um conjunto robusto de bibliotecas e ferramentas para desenvolvedores Java integrarem serviços da AWS em suas aplicações.
    - **.NET/C#:** O AWS SDK para .NET (AWS SDK for C#) permite que desenvolvedores .NET utilizem os serviços da AWS em suas aplicações, com suporte tanto para .NET Core quanto para .NET Framework.

2. **Instalação:**

   Depois de escolher o SDK apropriado para sua linguagem de programação, você pode instalá-lo usando gerenciadores de pacotes ou baixando o SDK diretamente.

    - **Python (Boto3):** Instale o Boto3 usando o pip, o gerenciador de pacotes Python:

    ```sh
    pip install boto3
    ```

    - **JavaScript/Node.js:** Instale o AWS SDK para JavaScript usando o npm, o gerenciador de pacotes do Node.js:

    ```sh
    npm install aws-sdk
    ```

    - **Java:** Adicione o AWS SDK para Java como dependência na configuração do seu projeto Maven ou Gradle, ou baixe os arquivos JAR do SDK diretamente no site da AWS.
    - **.NET/C#:** Instale o AWS SDK para .NET via NuGet, o gerenciador de pacotes do .NET, adicionando as referências de pacotes apropriadas ao seu projeto.

3. **Autenticação:**

   Antes de usar o SDK para interagir com os serviços da AWS, você precisa autenticar suas requisições. A AWS suporta vários métodos de autenticação, incluindo funções IAM, chaves de acesso e credenciais de segurança temporárias.

    - **Funções IAM:** Atribua funções IAM às instâncias EC2 da sua aplicação ou use usuários do AWS Identity and Access Management (IAM) para gerenciar o acesso aos recursos da AWS.
    - **Chaves de Acesso:** Gere chaves de acesso (Access Key ID e Secret Access Key) para usuários IAM e configure-as nas credenciais da sua aplicação.

4. **Código de Exemplo e Documentação:**

   Explore a documentação do SDK e exemplos de código fornecidos pela AWS para entender como usar o SDK para interagir com vários serviços da AWS. Cada SDK oferece documentação abrangente, incluindo guias, referências de API e exemplos para ajudá-lo a começar rapidamente.

    - **Python (Boto3):** Visite a documentação do Boto3 e explore os serviços e métodos disponíveis. Experimente snippets de código de exemplo para entender como realizar ações como criar instâncias EC2, fazer upload de arquivos para o S3 ou invocar funções Lambda.
    - **JavaScript/Node.js:** Confira a documentação do AWS SDK para JavaScript, que inclui guias e exemplos para trabalhar com os serviços da AWS em aplicações Node.js. Experimente códigos de exemplo para realizar tarefas como listar buckets S3, consultar tabelas DynamoDB ou enviar mensagens via SNS.
    - **Java/.NET/C#:** Da mesma forma, explore a documentação e exemplos de código fornecidos para os SDKs da AWS para Java e .NET/C#. Aprenda a inicializar clientes, fazer chamadas de API e manipular respostas dos serviços da AWS.

### Automatizando Tarefas e Fluxos de Trabalho na AWS usando CLI e SDKs:

1. **Scriptando com CLI:**

   Usando a AWS CLI, você pode criar scripts shell ou arquivos em lote para automatizar tarefas repetitivas e gerenciar recursos da AWS a partir da linha de comando. Veja como você pode automatizar tarefas da AWS usando scripts CLI:

    - **Scripts Shell:** Escreva scripts shell usando Bash ou PowerShell que incorporem comandos da AWS CLI para realizar tarefas como lançar instâncias EC2, criar buckets S3, gerenciar usuários IAM e muito mais.
    - **Arquivos em Lote:** Em sistemas Windows, use arquivos em lote (.bat) para executar comandos da AWS CLI de forma sequencial ou condicional, automatizando tarefas como rotinas de backup, sincronização de dados e provisionamento de recursos.
    - **Parametrização:** Parametrize seus scripts para torná-los reutilizáveis e adaptáveis a diferentes ambientes. Use variáveis para armazenar IDs de recursos da AWS, credenciais e outros parâmetros de configuração.

2. **Integração com SDKs:**

   Além de scriptar com CLI, você pode integrar os SDKs da AWS no código da sua aplicação para automatizar tarefas da AWS de forma programática. Veja como você pode automatizar fluxos de trabalho na AWS usando integração com SDKs:

    - **Desenvolvimento de Aplicações:** Incorpore chamadas de SDK da AWS no código da sua aplicação para interagir diretamente com os serviços da AWS. Isso permite automatizar tarefas dentro das suas aplicações, como upload/download de arquivos, interações com banco de dados e processamento de eventos.
    - **Automação Orientada a Eventos

:** Use SDKs da AWS para construir fluxos de trabalho orientados a eventos que respondem a eventos dentro do seu ambiente AWS. Por exemplo, você pode acionar funções Lambda em resposta a uploads de objetos no S3, notificações SNS ou mudanças em streams DynamoDB.
- **Tarefas Agendadas:** Implemente tarefas agendadas usando SDKs da AWS para automatizar operações recorrentes, como backups de dados, rotação de logs ou escalabilidade de infraestrutura. Use serviços como AWS CloudWatch Events para agendar invocações Lambda ou ações de instâncias EC2.

3. **Infraestrutura como Código (IaC):**

   Combine a automação com CLI e SDK com ferramentas de Infraestrutura como Código (IaC), como AWS CloudFormation ou Terraform, para provisionar e gerenciar infraestrutura de forma declarativa. Veja como você pode automatizar infraestrutura usando IaC:

    - **Provisionamento Baseado em Templates:** Defina configurações de infraestrutura usando templates CloudFormation ou configurações Terraform. Esses templates descrevem o estado desejado dos seus recursos da AWS, incluindo instâncias EC2, bancos de dados RDS, VPCs e muito mais.
    - **Workflows de Automação:** Use scripts de automação CLI ou SDK para implantar e gerenciar stacks CloudFormation ou configurações Terraform. Automatize o processo de criação, atualização e exclusão de recursos com base em mudanças no seu código de infraestrutura.
    - **Controle de Versão:** Armazene o código de infraestrutura em repositórios de controle de versão (e.g., Git) para rastrear mudanças, colaborar com membros da equipe e impor melhores práticas para o gerenciamento de infraestrutura.

### Perguntas de Entrevista Baseadas em Cenários:

Aqui estão perguntas de entrevista baseadas em cenários cobrindo os tópicos de AWS CLI, SDKs e automação de tarefas e fluxos de trabalho na AWS:

**Pergunta 1:** Você pode descrever um cenário em que teve que usar a AWS CLI para automatizar uma tarefa rotineira?  
**Resposta:** Claro. Em um projeto anterior, tivemos a necessidade de automatizar backups diários das nossas instâncias EC2 para o Amazon S3. Criei um script shell usando comandos da AWS CLI que listava todas as instâncias EC2 em execução, identificava as que estavam marcadas para backup, criava snapshots dos volumes EBS e, em seguida, copiava os snapshots para um bucket S3 para armazenamento de longo prazo. Agendei este script para rodar como um cron job todas as noites, garantindo que nossos dados fossem consistentemente backupados sem a necessidade de intervenção manual.

**Pergunta 2:** Como você lidaria com autenticação e autorização ao usar a AWS CLI em um ambiente multi-conta?  
**Resposta:** Em um ambiente multi-conta, é essencial garantir a autenticação e autorização adequadas. Eu configuraria a AWS CLI com perfis separados para cada conta da AWS usando o comando `aws configure` e especificaria o perfil ao executar comandos usando a opção `--profile`. Além disso, eu aproveitaria funções IAM com permissões apropriadas atribuídas a elas em cada conta da AWS. Ao assumir funções IAM a partir da CLI, posso garantir que os comandos CLI operem dentro dos limites das permissões atribuídas.

**Pergunta 3:** Você pode fornecer um exemplo de um cenário onde utilizou os SDKs da AWS para automatizar uma tarefa dentro de uma aplicação?  
**Resposta:** Certamente. Em um projeto recente, precisávamos implementar um pipeline de processamento de imagens que envolvia o upload de imagens para o Amazon S3, redimensionamento das imagens e, em seguida, armazenamento das imagens redimensionadas de volta no S3. Usei o SDK da AWS para Python (Boto3) dentro da nossa aplicação Python para interagir com o S3. Especificamente, escrevi código para fazer upload de imagens, acionar funções Lambda para redimensionamento e gerenciar as imagens redimensionadas. Isso nos permitiu automatizar todo o fluxo de trabalho de processamento de imagens de forma integrada na nossa aplicação.

**Pergunta 4:** Como você lidaria com tratamento de erros e tentativas de repetição ao fazer chamadas de API usando os SDKs da AWS?  
**Resposta:** Tratamento de erros e tentativas de repetição são aspectos cruciais para a construção de aplicações robustas com os SDKs da AWS. Eu implementaria o tratamento de erros capturando exceções levantadas por operações do SDK e lidando com elas adequadamente, como registrando erros e tomando ações corretivas. Além disso, eu configuraria tentativas automáticas para chamadas de API usando recursos do SDK, como backoff exponencial com jitter. Isso ajuda a mitigar erros transitórios e garantir a confiabilidade das nossas aplicações, mesmo em face de problemas intermitentes de conectividade ou interrupções de serviço.

**Pergunta 5:** Descreva um cenário em que você usou automação para otimizar a utilização de recursos e a eficiência de custos na AWS.  
**Resposta:** Em um projeto anterior, implementamos uma solução de autoescalonamento para nossas instâncias EC2 para ajustar dinamicamente a capacidade com base na demanda de carga de trabalho. Usamos métricas do AWS CloudWatch para monitorar a utilização de CPU e, quando os limites foram excedidos, acionamos funções Lambda para escalar instâncias EC2 para cima ou para baixo conforme necessário. Esta automação nos ajudou a otimizar a utilização de recursos provisionando instâncias apenas quando necessário, resultando em economias significativas de custos ao eliminar a capacidade ociosa.

**Pergunta 6:** Como você abordaria a automação do deployment de uma aplicação baseada em microsserviços na AWS?  
**Resposta:** Automatizar o deployment de uma aplicação baseada em microsserviços envolve orquestrar o provisionamento de vários recursos da AWS, como instâncias EC2, clusters ECS, bancos de dados RDS e mais. Eu usaria ferramentas de Infraestrutura como Código (IaC) como AWS CloudFormation ou Terraform para definir o estado desejado da infraestrutura. Escrevendo templates ou configurações que especificam a arquitetura e as dependências da aplicação, posso automatizar o processo de deployment, garantindo consistência e repetibilidade entre ambientes. Além disso, eu aproveitaria pipelines CI/CD com ferramentas como AWS CodePipeline e CodeDeploy para automatizar as fases de build, teste e deployment, permitindo a integração contínua e entrega de atualizações para a aplicação.

### Conclusão:

Dominando a AWS CLI e os SDKs, você estará equipado para otimizar suas operações na nuvem e acelerar seus fluxos de trabalho de desenvolvimento. Seja você um aficionado por linha de comando ou prefira interações programáticas, a AWS fornece as ferramentas que você precisa para automatizar com facilidade. Então, arremangue-se, mergulhe na documentação e comece a automatizar suas tarefas na AWS hoje mesmo!

Fique atento para a lição de amanhã, onde exploraremos outros conceitos da AWS. Boa automação!