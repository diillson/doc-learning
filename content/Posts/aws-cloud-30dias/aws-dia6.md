---
title: "Dia 6: RDS (Relational Database Service)"
date: 2024-08-03
tags: ["AWS", "RDS", "Cloud Computing", "Database", "Treinamento"]
description: "Explore o Amazon RDS, entenda suas funcionalidades, como iniciar e configurar instâncias RDS e conectá-las a instâncias EC2."
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia6"]
author: ["Edilson Freitas"]
cover:
   image: images/rds.jpeg
   hiddenInList: true
---

## Bem-vindo ao Dia 6 da nossa jornada de 30 dias pela AWS!

Hoje, mergulharemos no coração dos bancos de dados relacionais na nuvem com o Amazon RDS. Exploraremos os fundamentos do RDS, seus benefícios e como começar a lançar e configurar instâncias RDS. Além disso, veremos como conectar instâncias RDS a instâncias EC2.

### Introdução ao RDS e Serviços de Banco de Dados Gerenciados

Vamos nos aprofundar na introdução ao RDS e aos serviços de banco de dados gerenciados.

#### Introdução ao RDS (Relational Database Service)
Amazon Relational Database Service (RDS) é um serviço de banco de dados totalmente gerenciado fornecido pela AWS. Ele permite que os usuários configurem, operem e dimensionem bancos de dados relacionais na nuvem sem se preocupar com a infraestrutura subjacente. O RDS automatiza tarefas rotineiras de banco de dados, como provisionamento de hardware, configuração de banco de dados, aplicação de patches e backups, permitindo que os desenvolvedores se concentrem mais em suas aplicações e menos na gestão de bancos de dados.

##### Principais Recursos do RDS:

- **Suporte a Múltiplos Motores de Banco de Dados:** O RDS suporta vários motores de banco de dados populares, incluindo MySQL, PostgreSQL, MariaDB, Oracle, SQL Server e Amazon Aurora. Essa flexibilidade permite que os usuários escolham o motor que melhor atenda aos requisitos de sua aplicação.
- **Backups Automatizados e Recuperação Pontual:** O RDS realiza automaticamente backups dos seus bancos de dados conforme o período de retenção especificado. Ele também permite a recuperação pontual, possibilitando restaurar seu banco de dados para qualquer ponto específico dentro do período de retenção.
- **Alta Disponibilidade e Replicação:** O RDS fornece recursos de alta disponibilidade, como implantações Multi-AZ (Availability Zone) e réplicas de leitura. As implantações Multi-AZ replicam seu banco de dados de forma síncrona entre várias zonas de disponibilidade para garantir durabilidade e tolerância a falhas, enquanto as réplicas de leitura permitem descarregar o tráfego de leitura da instância principal do banco de dados, melhorando o desempenho e a escalabilidade.
- **Segurança e Conformidade:** O RDS oferece vários recursos de segurança para ajudar a proteger seus bancos de dados, incluindo isolamento de rede usando Amazon VPC, criptografia em repouso usando AWS KMS (Key Management Service) e criptografia SSL para dados em trânsito. O RDS também suporta mecanismos de autenticação de banco de dados, como autenticação IAM e autenticação tradicional com nome de usuário/senha.
- **Escalabilidade e Desempenho:** Com o RDS, você pode facilmente dimensionar sua instância de banco de dados verticalmente (aumentando o tamanho da instância) ou horizontalmente (adicionando réplicas de leitura). O RDS também fornece métricas de monitoramento de desempenho e ferramentas para ajudar a otimizar o desempenho do banco de dados.

#### Serviços de Banco de Dados Gerenciados

Os serviços de banco de dados gerenciados como o RDS abstraem grande parte da sobrecarga operacional associada à gestão tradicional de bancos de dados. Eles oferecem os seguintes benefícios:

- **Administração Simplificada de Banco de Dados:** Os serviços de banco de dados gerenciados lidam com tarefas rotineiras de administração de banco de dados, como provisionamento, aplicação de patches, backups e monitoramento, liberando desenvolvedores e DBAs para se concentrarem no desenvolvimento de aplicações e na lógica de negócios.
- **Alta Disponibilidade e Confiabilidade:** Os serviços gerenciados geralmente oferecem recursos integrados de alta disponibilidade, como failover automático, replicação de dados e capacidades de backup/restauração, garantindo que seus bancos de dados sejam altamente disponíveis e confiáveis.
- **Escalabilidade e Desempenho:** Os serviços gerenciados facilitam a escalabilidade de seus bancos de dados conforme a demanda. Eles frequentemente fornecem ferramentas e recursos para otimização e monitoramento de desempenho, ajudando a manter o desempenho ideal do banco de dados.
- **Segurança e Conformidade:** Os serviços de banco de dados gerenciados oferecem robustos recursos de segurança e certificações de conformidade para ajudar a atender aos requisitos de segurança e regulatórios. Eles lidam com a aplicação de patches de segurança, criptografia, controle de acesso e auditoria, reduzindo o risco de violações de segurança e perda de dados.

### Lançando Instâncias RDS e Configurando Parâmetros

Esses são passos fundamentais para configurar bancos de dados relacionais usando o Amazon RDS. Aqui está um guia detalhado sobre como lançar instâncias RDS e configurar parâmetros:

#### Lançando Instâncias RDS:

1. **Navegue até o Console RDS:** Faça login no seu Console de Gerenciamento da AWS e navegue até o serviço RDS.

2. **Clique em “Create database”:** No painel do RDS, clique no botão “Create database” para iniciar o processo de criação da instância.

3. **Escolha o Motor e a Versão:** Selecione o motor de banco de dados que você deseja usar (por exemplo, MySQL, PostgreSQL, Oracle, SQL Server) e escolha a versão que melhor atenda aos requisitos da sua aplicação.

4. **Especifique Detalhes da Instância:**

    - **DB Instance Class:** Escolha a classe de instância apropriada com base nos requisitos de computação e memória.
    - **Implantação Multi-AZ:** Opcionalmente, selecione a implantação Multi-AZ para alta disponibilidade e redundância em várias zonas de disponibilidade.
    - **Tipo de Armazenamento e Armazenamento Alocado:** Selecione o tipo de armazenamento (por exemplo, SSD de Propósito Geral, SSD IOPS Provisionado) e especifique o espaço de armazenamento alocado para seu banco de dados.
    - **Identificador da Instância DB:** Forneça um identificador exclusivo para sua instância RDS.

5. **Configurar Configurações Avançadas:**

    - **Rede e Segurança:** Escolha a Virtual Private Cloud (VPC) onde você deseja lançar sua instância RDS. Configure o grupo de sub-redes e especifique grupos de segurança para controlar o tráfego de entrada e saída.
    - **Opções de Banco de Dados:** Defina o nome do banco de dados, porta e grupo de parâmetros (opcional).
    - **Backup:** Configure backups automatizados e especifique o período de retenção para o armazenamento de backups.
    - **Monitoramento:** Habilite o monitoramento aprimorado para coletar métricas adicionais para sua instância RDS.
    - **Manutenção:** Especifique a janela de manutenção preferida para aplicar patches e atualizações à sua instância de banco de dados.

6. **Adicionar Autenticação e Criptografia do Banco de Dados:**

    - Defina o nome de usuário e a senha do mestre para sua instância RDS.
    - Habilite a criptografia em repouso usando o AWS Key Management Service (KMS) para maior segurança dos dados.

7. **Revisar e Lançar:**

    - Verifique todas as configurações que você fez para sua instância RDS.
    - Clique no botão “Create database” para lançar sua instância RDS.

#### Configurando Parâmetros:

Depois de lançar sua instância RDS, você pode precisar configurar parâmetros adicionais com base nos requisitos da sua aplicação. Veja como você pode configurar parâmetros para sua instância RDS:

1. **Grupos de Parâmetros:** Os grupos de parâmetros do RDS contêm configurações que governam o comportamento da sua instância de banco de dados. Você pode criar grupos de parâmetros personalizados ou usar os grupos de parâmetros padrão fornecidos pela AWS.

2. **Modificar Parâmetros:**

    - Navegue até o painel do RDS e selecione sua instância RDS.
    - Na aba “Configuration”, clique em “Modify” para alterar as configurações de parâmetros.
    - Você pode modificar vários parâmetros, como configurações do motor de banco de dados, alocação de memória, opções de log e parâmetros de desempenho.

3. **Aplicar Alterações:**

    - Após modificar os parâmetros, reveja as mudanças e clique em “Apply immediately” ou escolha uma janela de manutenção para aplicar as mudanças.
    - O AWS RDS aplicará as alterações de parâmetros à sua instância de banco de dados sem causar tempo de inatividade.

4. **Monitorar Desempenho:** Monitore o desempenho da sua instância RDS após aplicar as mudanças de parâmetros para garantir que seu banco de dados esteja operando de forma otimizada.

### Conectando-se a Instâncias RDS a Partir de EC2

É um cenário comum em aplicações baseadas na nuvem onde você pode ter seus servidores de aplicação (instâncias EC2) acessando bancos de dados hospedados no RDS. Aqui está um guia passo a passo sobre como conectar-se a instâncias RDS a partir de instâncias EC2:

#### Pré-requisitos:

- **Ambas as instâncias RDS e EC2 devem estar na mesma VPC:** Certifique-se de que sua instância RDS e a instância EC2 estejam implantadas dentro da mesma Virtual Private Cloud

 (VPC) para permitir a comunicação de rede entre elas.
- **Configuração do Grupo de Segurança:** Configure o grupo de segurança associado à sua instância RDS para permitir o tráfego de entrada do grupo de segurança associado à sua instância EC2 na porta apropriada do banco de dados (por exemplo, 3306 para MySQL, 5432 para PostgreSQL).

#### Passos para Conectar-se ao RDS a partir da EC2:

1. **Identificar o Endpoint e a Porta do RDS:**

    - Faça login no Console de Gerenciamento da AWS e navegue até o serviço RDS.
    - Selecione sua instância RDS e anote o endpoint (por exemplo, my-database-instance.abcdefg123.us-west-2.rds.amazonaws.com) e o número da porta (o padrão é 3306 para MySQL, 5432 para PostgreSQL).

2. **Instalar o Cliente do Banco de Dados na Instância EC2:**

    - Conecte-se à sua instância EC2 usando SSH.
    - Instale o cliente de banco de dados apropriado para o seu motor de banco de dados RDS (por exemplo, cliente MySQL para bancos de dados MySQL, cliente PostgreSQL para bancos de dados PostgreSQL). Você pode instalar esses clientes usando gerenciadores de pacotes como apt (para Ubuntu) ou yum (para Amazon Linux).

3. **Conectar-se Usando a Linha de Comando:**

    - Uma vez que o cliente de banco de dados esteja instalado, você pode se conectar à sua instância RDS a partir da linha de comando usando a seguinte sintaxe:

    Para MySQL:

    ```bash
    mysql -h <RDS_endpoint> -P <port> -u <username> -p
    ```

    Para PostgreSQL:

    ```bash
    psql -h <RDS_endpoint> -p <port> -U <username> -d <database_name>
    ```

    Substitua `<RDS_endpoint>`, `<port>`, `<username>` e `<database_name>` pelo seu endpoint RDS real, porta, nome de usuário e nome do banco de dados, respectivamente.

4. **Fornecer Credenciais:**

    - Quando você executar o comando, será solicitado que insira a senha para o usuário especificado. Insira a senha associada ao nome de usuário que você forneceu.

5. **Verificação:**

    - Após conectar-se com sucesso, você será apresentado com um prompt ou console de banco de dados, indicando que você está conectado à sua instância RDS a partir da sua instância EC2.
    - Agora você pode executar consultas SQL, realizar operações de banco de dados e interagir com seu banco de dados RDS conforme necessário a partir da sua instância EC2.

### Exemplos de Código

#### Exemplo: Lançando uma Instância RDS (Usando AWS CLI)

```bash
aws rds create-db-instance \
    --db-instance-identifier mydbinstance \
    --db-instance-class db.t2.micro \
    --engine mysql \
    --allocated-storage 20 \
    --master-username mymasteruser \
    --master-user-password mymasterpassword \
    --availability-zone us-west-2a \
    --backup-retention-period 7 \
    --port 3306 \
    --multi-az \
    --engine-version 5.7
```

#### Exemplo: Configurando Parâmetros (Usando AWS CLI)

```bash
aws rds modify-db-parameter-group \
    --db-parameter-group-name mydbparametergroup \
    --parameters "ParameterName=innodb_buffer_pool_size,ParameterValue=67108864,ApplyMethod=immediate" \
                 "ParameterName=max_connections,ParameterValue=200,ApplyMethod=immediate"
```

#### Exemplo: Conectando-se à Instância RDS a partir da EC2 (Usando Cliente MySQL)

1. **Instalar Cliente MySQL na Instância EC2:**
   Para Ubuntu/Debian:

```bash
sudo apt-get update
sudo apt-get install mysql-client -y
```

Para Amazon Linux:

```bash
sudo yum update
sudo yum install mysql -y
```

2. **Conectar-se à Instância RDS:**
   Para MySQL:

```bash
mysql -h mydbinstance.abcdefg123.us-west-2.rds.amazonaws.com -P 3306 -u mymasteruser -p
```

Você será solicitado a inserir a senha para o usuário mestre (‘mymasteruser’). Após inserir a senha, você será conectado ao prompt do MySQL onde poderá executar consultas SQL.

### Questões de Entrevista Baseadas em Cenários para Engenheiros DevOps com Foco no AWS RDS

#### Cenário: Você pode explicar o processo de lançamento de uma instância RDS usando o Console de Gerenciamento da AWS?
**Resposta:** Para lançar uma instância RDS via Console de Gerenciamento da AWS, siga estes passos:

- Faça login no Console de Gerenciamento da AWS e navegue até o serviço RDS.
- Clique em “Create database” e escolha o motor de banco de dados (por exemplo, MySQL, PostgreSQL).
- Configure os detalhes da instância, como classe de instância, tipo de armazenamento, armazenamento alocado e identificador da instância DB.
- Configure configurações adicionais como VPC, grupo de sub-redes, nome do banco de dados e porta.
- Especifique os detalhes de autenticação do banco de dados (nome de usuário e senha) e as configurações de criptografia.
- Revise suas configurações e clique em “Launch DB instance” para iniciar o processo de criação da instância.

#### Cenário: Quais são algumas considerações a serem mantidas em mente ao selecionar a classe de instância para uma instância RDS?
**Resposta:** Ao selecionar a classe de instância para uma instância RDS, considere fatores como CPU, memória, capacidade de armazenamento e requisitos de carga de trabalho previstos. Escolha uma classe de instância que possa lidar eficientemente com a carga de trabalho da sua aplicação, garantindo escalabilidade e relação custo-benefício. Além disso, considere fatores como implantação Multi-AZ para alta disponibilidade e réplicas de leitura para escalabilidade.

#### Cenário: Como você modifica os parâmetros do RDS usando o AWS CLI?
**Resposta:** Para modificar os parâmetros do RDS usando o AWS CLI, você pode usar o comando ‘modify-db-parameter-group’. Aqui está um exemplo de comando:

```bash
aws rds modify-db-parameter-group \
    --db-parameter-group-name mydbparametergroup \
    --parameters "ParameterName=innodb_buffer_pool_size,ParameterValue=67108864,ApplyMethod=immediate" \
                "ParameterName=max_connections,ParameterValue=200,ApplyMethod=immediate"
```

Este comando modifica os parâmetros especificados no grupo de parâmetros dado (‘mydbparametergroup’) com efeito imediato.

#### Cenário: Por que é importante revisar cuidadosamente as mudanças de parâmetros antes de aplicá-las a uma instância RDS?
**Resposta:** É crucial revisar as mudanças de parâmetros antes de aplicá-las a uma instância RDS para evitar possíveis interrupções no ambiente do banco de dados. Valores de parâmetros incorretos ou configurações incorretas podem impactar o desempenho, a disponibilidade e a integridade dos dados do banco de dados. Ao revisar as mudanças, você pode garantir que as novas configurações de parâmetros estejam alinhadas com os requisitos da sua aplicação e as melhores práticas.

#### Cenário: Quais são os passos necessários para conectar-se a uma instância RDS a partir de uma instância EC2?
**Resposta:** Para conectar-se a uma instância RDS a partir de uma instância EC2, siga estes passos:

- Certifique-se de que ambas as instâncias RDS e EC2 estão na mesma VPC.
- Configure os grupos de segurança associados a ambas as instâncias para permitir o tráfego de entrada na porta apropriada do banco de dados (por exemplo, 3306 para MySQL, 5432 para PostgreSQL).
- Instale o cliente de banco de dados (por exemplo, cliente MySQL) na instância EC2.
- Use o cliente de banco de dados para conectar-se à instância RDS especificando o endpoint, porta, nome de usuário e senha.

#### Cenário: Como você solucionaria problemas de conectividade entre uma instância EC2 e uma instância RDS?
**Resposta:** Para solucionar problemas de conectividade entre uma instância EC2 e uma instância RDS, você pode realizar os seguintes passos:

- Verifique se os grupos de segurança associados a ambas as instâncias permitem o tráfego de entrada na porta correta.
- Certifique-se de que as ACLs de rede (se aplicável) permitem o tráfego entre as instâncias.
- Verifique as tabelas de rotas e a configuração do gateway de internet para garantir o roteamento de rede adequado.
- Confirme se a instância RDS está no estado disponível e acessível pela rede.
- Use ferramentas como telnet ou nc para testar a conectividade com a instância RDS a partir da instância EC2.
- Revise os logs da instância RDS e as métricas do CloudWatch para identificar erros ou problemas que possam indicar problemas de conectividade.

### Conclusão

Parabéns por completar o Dia 6 da nossa jornada pela AWS! Hoje, cobrimos os fundamentos do Amazon RDS, desde o lançamento de instâncias até a conexão com elas a partir de instâncias EC2. Os serviços de banco de dados gerenciados como o RDS permitem que os desenvolvedores se concentrem em construir aplicações enquanto delegam a gestão pesada de bancos de dados para a AWS.

Fique atento para mais aventuras emocionantes na AWS amanhã! Feliz computação em nuvem!