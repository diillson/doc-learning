---
title: "Dia 30: Preparação e Revisão para o Exame de Certificação AWS"
date: "2024-09-04"
description: "Prepare-se para o exame de certificação AWS revisando conceitos e serviços-chave, praticando com perguntas de exemplo e aprimorando suas estratégias de exame."
categories: ["Cloud"]
tags: ["AWS", "Certificação", "Exame", "Revisão", "Preparação"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia30"]
author: ["Edilson Freitas"]
cover:
  image: images/preparationaws.png
  hiddenInList: true
---

# Parabéns! 

Você chegou ao último dia da sua jornada de 30 dias no curso sobre AWS. 
Hoje, focaremos na preparação para o seu exame de certificação AWS.
Este dia é crucial para solidificar seu entendimento dos principais conceitos, praticar com perguntas de exemplo e aprimorar suas estratégias para fazer o exame.

### Revisão de Conceitos e Serviços-Chave da AWS

Vamos revisar mais profundamente os conceitos e serviços-chave da AWS para ajudá-lo a se preparar para o exame de certificação:

#### 1. Serviços de Computação:

**Amazon EC2 (Elastic Compute Cloud):**
- **EC2** fornece capacidade de computação redimensionável na nuvem.
- Você pode escolher entre vários tipos de instâncias otimizadas para diferentes cargas de trabalho.
- **Exemplo:** Lançamento de um servidor web usando EC2 para hospedar um site.

**AWS Lambda:**
- **Lambda** permite executar código sem provisionar ou gerenciar servidores.
- Ele escala automaticamente com base em solicitações ou eventos recebidos.
- **Exemplo:** Criação de uma função Lambda para processar arquivos carregados em um bucket S3.

**Amazon ECS (Elastic Container Service):**
- **ECS** é um serviço de orquestração de contêineres totalmente gerenciado.
- Permite executar contêineres Docker em escala.
- **Exemplo:** Implantação de uma arquitetura de microsserviços usando ECS para gerenciar aplicações em contêineres.

#### 2. Serviços de Armazenamento:

**Amazon S3 (Simple Storage Service):**
- **S3** fornece armazenamento de objetos com alta durabilidade e disponibilidade.
- É adequado para armazenar e recuperar qualquer quantidade de dados.
- **Exemplo:** Armazenamento de arquivos multimídia, como imagens, vídeos e documentos em buckets S3.

**Amazon EBS (Elastic Block Store):**
- **EBS** oferece volumes de armazenamento em nível de bloco para uso com instâncias EC2.
- Ele fornece armazenamento persistente que permanece independentemente da vida útil de uma instância.
- **Exemplo:** Anexar um volume EBS a uma instância EC2 para armazenar dados da aplicação.

**Amazon Glacier:**
- **Glacier** é um serviço de armazenamento de baixo custo para arquivamento de dados e backup de longo prazo.
- É projetado para dados que são raramente acessados e requerem retenção de longo prazo.
- **Exemplo:** Arquivamento de logs históricos e backups para conformidade regulatória usando Glacier.

#### 3. Rede:

**Amazon VPC (Virtual Private Cloud):**
- **VPC** permite provisionar uma seção logicamente isolada da Nuvem AWS.
- Ele permite que você defina sua topologia de rede virtual, incluindo sub-redes, tabelas de rotas e gateways de rede.
- **Exemplo:** Criação de uma VPC com sub-redes públicas e privadas para hospedar aplicações multi-camadas de forma segura.

**Grupos de Segurança:**
- **Grupos de Segurança** atuam como firewalls virtuais para suas instâncias EC2 para controlar o tráfego de entrada e saída.
- Você pode definir regras para permitir ou negar tráfego com base em protocolos, portas e endereços IP.
- **Exemplo:** Configuração de grupos de segurança para permitir tráfego HTTP (porta 80) para um servidor web, mas restringir o acesso SSH (porta 22).

**Amazon Route 53:**
- **Route 53** é um serviço de sistema de nomes de domínio (DNS) escalável.
- Ele permite rotear o tráfego para recursos AWS ou pontos finais externos com base em várias políticas de roteamento.
- **Exemplo:** Configuração do Route 53 para rotear o tráfego de entrada para diferentes regiões AWS com base na latência ou geolocalização.

#### 4. Bancos de Dados:

**Amazon RDS (Relational Database Service):**
- **RDS** oferece serviços de banco de dados relacional gerenciado para MySQL, PostgreSQL, Oracle, SQL Server e MariaDB.
- Ele cuida de tarefas de banco de dados rotineiras, como provisionamento, aplicação de patches, backup e recuperação.
- **Exemplo:** Implantação de um banco de dados MySQL Multi-AZ usando RDS para alta disponibilidade e tolerância a falhas.

**Amazon DynamoDB:**
- **DynamoDB** é um serviço de banco de dados NoSQL totalmente gerenciado.
- Ele fornece escalabilidade, desempenho e acesso a dados de baixa latência de forma transparente.
- **Exemplo:** Construção de um placar de jogos em tempo real usando DynamoDB para armazenar pontuações e classificações de jogadores.

**Amazon Redshift:**
- **Redshift** é um serviço de data warehouse totalmente gerenciado.
- Ele permite analisar grandes conjuntos de dados usando consultas SQL e ferramentas de inteligência de negócios.
- **Exemplo:** Carregamento e consulta de dados de vendas de várias fontes para análises de negócios usando Redshift.

Revisando e entendendo esses conceitos e serviços-chave da AWS, você estará mais preparado para enfrentar perguntas e cenários relacionados a computação, armazenamento, rede e bancos de dados.

### Perguntas de Exemplo:

#### 1. Serviços de Computação:

**Pergunta:** Qual serviço AWS você usaria para implantar uma aplicação serverless que escala automaticamente com base no tráfego recebido e executa código em resposta a eventos?
- A) Amazon EC2
- B) Amazon S3
- C) AWS Lambda
- D) Amazon RDS

**Resposta:** C) AWS Lambda  
**Explicação:** O AWS Lambda é um serviço de computação serverless que escala automaticamente para lidar com solicitações ou eventos recebidos. É ideal para implantar aplicações serverless que exigem escalabilidade e execução baseada em eventos.

#### 2. Serviços de Armazenamento:

**Pergunta:** Qual serviço de armazenamento da AWS é mais adequado para armazenar dados de aplicação frequentemente acessados que requerem alta durabilidade e disponibilidade?
- A) Amazon S3
- B) Amazon EBS
- C) Amazon Glacier
- D) Amazon DynamoDB

**Resposta:** A) Amazon S3  
**Explicação:** O Amazon S3 (Simple Storage Service) fornece armazenamento de objetos com alta durabilidade e disponibilidade. É adequado para armazenar e recuperar qualquer quantidade de dados, incluindo dados de aplicação frequentemente acessados.

#### 3. Rede:

**Pergunta:** Qual serviço da AWS permite que você crie uma seção privada, isolada da Nuvem AWS com sua própria topologia de rede virtual, incluindo sub-redes, tabelas de rotas e configurações de segurança?
- A) Amazon Route 53
- B) Amazon VPC
- C) AWS Direct Connect
- D) Amazon CloudFront

**Resposta:** B) Amazon VPC  
**Explicação:** O Amazon VPC (Virtual Private Cloud) permite provisionar uma seção logicamente isolada da Nuvem AWS com sua própria topologia de rede virtual. Você pode definir sub-redes, tabelas de rotas, grupos de segurança e gateways de rede dentro de uma VPC.

### Cenário de Exemplo:

**Você é responsável por projetar uma arquitetura para uma aplicação web que exige alta disponibilidade e tolerância a falhas. A aplicação consiste em um servidor web de front-end, um servidor API de back-end e um banco de dados. Os usuários devem poder acessar a aplicação de qualquer lugar do mundo com latência mínima.**
**Pergunta:** Quais serviços AWS você usaria e como arquitetaria a solução para atender aos requisitos de alta disponibilidade, tolerância a falhas e acesso de baixa latência?

**Resposta:**
Para atender aos requisitos de alta disponibilidade, tolerância a falhas e acesso de baixa latência, eu arquitetaria a solução da seguinte forma:

- **Servidor Web de Front-end:** Implantar várias instâncias do Amazon EC2 dentro de um grupo de Auto Scaling em várias Zonas de Disponibilidade (AZs) para garantir alta disponibilidade e tolerância a falhas. Usar um Application Load Balancer (ALB) para distribuir o tráfego de entrada entre as instâncias EC2.
- **Servidor API de Back-end:** Containerizar o servidor API usando AWS Fargate ou Amazon ECS para simplificar a implantação e o dimensionamento. Utilizar Amazon RDS para armazenamento de banco de dados, configurado com implantação Multi-AZ para failover automático e alta disponibilidade.
- **Entrega Global de Conteúdo:** Utilizar Amazon CloudFront, a rede de entrega de conteúdo (CDN) da AWS, para armazenar em cache e entregar conteúdo estático e dinâmico aos usuários com baixa latência. Configurar o CloudFront para distribuir conteúdo a partir de locais de borda ao redor do mundo.
- **Isolamento e Segurança de Rede:** Criar uma Amazon VPC dedicada para isolar recursos e definir grupos de segurança para controlar o tráfego de entrada e saída. Usar AWS Identity and Access Management (IAM) para gerenciar o acesso e permissões de usuários.

Implementando essa arquitetura, a aplicação web se beneficiará de alta disponibilidade, tolerância a falhas e acesso de baixa latência para usuários em todo o mundo.

### Dicas para Fazer o Exame de Certificação AWS

Finalmente, vamos discutir algumas dicas valiosas para ter em mente ao fazer o exame de certificação AWS:

- **Gerenciamento do Tempo:** Administre seu tempo de forma eficaz durante o exame. Leia as perguntas com cuidado, mas evite gastar muito tempo em uma única pergunta. Marque perguntas difíceis para revisão e retorne a elas mais tarde, se o tempo permitir.
- **Entenda os Formatos das Perguntas:** Os exames de certificação AWS incluem vários formatos de perguntas, como múltipla escolha, múltipla resposta e perguntas baseadas em cenários. Familiarize-se com esses formatos para saber como abordar cada pergunta.
- **Elimine Alternativas Incorretas:** Se você não tiver certeza sobre a resposta correta para uma pergunta, tente eliminar alternativas obviamente incorretas primeiro. Isso aumenta suas chances de selecionar a resposta correta, mesmo que você não tenha certeza.
- **Revise o Guia do Exame:** Antes do dia do exame, revise o Guia Oficial de Exames de Certificação da AWS para a certificação escolhida. Preste atenção especial aos tópicos cobertos e certifique-se de que tem uma compreensão sólida de cada um deles.

Lembre-se, a preparação é a chave para o sucesso. Confie no seu conhecimento e instintos, e você se sairá muito bem no seu exame de certificação AWS!

Boa sorte na sua jornada de certificação! 🚀