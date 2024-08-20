---
title: "Dia 15: Amazon ECS (Elastic Container Service)"
date: "2024-08-20"
description: "O ECS é uma ferramenta poderosa para implantar e gerenciar aplicações containerizadas."
categories: ["Cloud"]
tags: ["ECS", "docker", "container", "fargate"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia15"]
author: ["Edilson Freitas"]
cover:
  image: images/ecs.png
  hiddenInList: true
---


## Bem-vindo de volta à nossa jornada pela AWS! 

Hoje marcamos um ponto crucial ao mergulharmos no Amazon ECS, o Elastic Container Service da Amazon. O ECS é uma ferramenta poderosa para implantar e gerenciar aplicações containerizadas, proporcionando escalabilidade, confiabilidade e facilidade de gerenciamento. Nesta edição, cobriremos os conceitos essenciais de conteinerização, noções básicas do Docker e orientaremos você na implantação de suas aplicações usando o ECS.

Confira também as perguntas de entrevista baseadas em cenários no final deste blog. Se precisar de respostas para essas perguntas, não hesite em nos avisar!

### Compreendendo a Conteinerização e Noções Básicas do Docker:

Vamos aprofundar na compreensão da conteinerização e nas noções básicas do Docker:

#### Compreendendo a Conteinerização:

1. **Virtualização Leve**:
    - A conteinerização é uma forma de virtualização leve que permite empacotar uma aplicação e suas dependências em uma unidade padronizada conhecida como container.
    - Diferente das máquinas virtuais tradicionais (VMs), os containers compartilham o kernel do sistema operacional do host, tornando-os mais leves e eficientes.

2. **Isolamento e Consistência**:
    - Os containers fornecem isolamento para aplicações, garantindo que elas funcionem de forma independente, sem interferências.
    - A conteinerização garante consistência entre diferentes ambientes, desde o desenvolvimento até a produção, ao empacotar tudo que uma aplicação precisa para rodar, incluindo bibliotecas, dependências e tempo de execução.

3. **Portabilidade e Escalabilidade**:
    - Os containers são portáteis, o que significa que podem ser executados em qualquer plataforma ou ambiente de nuvem que suporte tecnologia de conteinerização, como Docker ou Kubernetes.
    - A conteinerização permite escalabilidade horizontal, permitindo implantar várias instâncias da sua aplicação rapidamente e eficientemente para atender à demanda crescente.

#### Noções Básicas do Docker:

1. **Docker Engine**:
    - O Docker é uma plataforma que fornece ferramentas para construir, enviar e executar containers. No seu núcleo está o Docker Engine, um ambiente de runtime para containers.
    - O Docker Engine consiste em um processo daemon (dockerd) que gerencia containers, imagens, redes e volumes.

2. **Imagem Docker**:
    - Uma imagem Docker é um pacote leve, autônomo e executável que contém tudo o que é necessário para executar um software, incluindo código, tempo de execução, bibliotecas e dependências.
    - As imagens são construídas usando um Dockerfile, que contém instruções para criar a imagem camada por camada.

3. **Container Docker**:
    - Um container Docker é uma instância de uma imagem Docker que é executada como um processo na máquina host.
    - Os containers são ambientes isolados que garantem que as aplicações sejam executadas de forma consistente em diferentes ambientes, independentemente da infraestrutura subjacente.

4. **Dockerfile**:
    - Um Dockerfile é um arquivo de texto que contém instruções para construir uma imagem Docker.
    - Ele especifica a imagem base, dependências, variáveis de ambiente e comandos necessários para configurar a imagem.

5. **CLI Docker**:
    - O Docker fornece uma interface de linha de comando (CLI) que permite interagir com o Docker Engine e executar várias operações, como construir imagens, executar containers e gerenciar objetos Docker.

6. **Docker Registry**:
    - Docker Registry é um repositório para imagens Docker, onde você pode armazenar e compartilhar suas imagens personalizadas.
    - O Docker Hub é um registro público fornecido pelo Docker, enquanto registros privados permitem que organizações armazenem imagens de forma privada dentro de sua infraestrutura.

7. **Docker Compose**:
    - O Docker Compose é uma ferramenta para definir e executar aplicações Docker com múltiplos containers.
    - Ele usa um arquivo YAML (docker-compose.yml) para especificar os serviços, redes e volumes necessários para a aplicação, facilitando o gerenciamento de configurações complexas do Docker.

### Implantando Aplicações Containerizadas Usando ECS:

Implantar aplicações containerizadas usando o Amazon ECS (Elastic Container Service) envolve vários passos importantes. Vamos detalhar o processo:

#### Passo 1: Configurando o Cluster ECS

1. **Criar Cluster ECS**:
    - Navegue até o console do ECS no Console de Gerenciamento da AWS.
    - Clique em "Criar Cluster" e escolha o modelo de cluster que atende às suas necessidades (EC2 ou Fargate).
    - Configure as definições do cluster, incluindo o nome do cluster, tipo de instância, número de instâncias (se estiver usando EC2) e opções de rede.

2. **Configurar Rede (Opcional)**:
    - Defina a configuração de rede para o seu cluster ECS, incluindo VPC, sub-redes, grupos de segurança e, opcionalmente, balanceadores de carga.

#### Passo 2: Criando uma Definição de Tarefa

1. **Definir Definição de Tarefa**:
    - As definições de tarefa especificam parâmetros para executar containers Docker como tarefas dentro do ECS.
    - Navegue até o console do ECS e clique em "Definições de Tarefa" na seção "Amazon ECS".
    - Clique em "Criar nova Definição de Tarefa" e escolha o tipo de lançamento (EC2 ou Fargate).
    - Especifique as definições de container, incluindo imagem Docker, limites de CPU/memória, variáveis de ambiente, rede e volumes de armazenamento.

2. **Configurar Função de Execução de Tarefa**:
    - Defina uma função IAM que conceda permissões ao ECS para executar ações em seu nome, como puxar imagens Docker do Amazon ECR (Elastic Container Registry).

#### Passo 3: Lançando Serviços

1. **Criar Serviço**:
    - Os serviços permitem que você execute e mantenha um número especificado de instâncias de uma definição de tarefa dentro do seu cluster ECS.
    - Navegue até o console do ECS e clique em "Clusters" para selecionar seu cluster.
    - Clique em "Criar Serviço" e especifique as configurações do serviço, incluindo a definição de tarefa, número desejado de tarefas, tipo de implantação e opções de balanceamento de carga.

2. **Configurar Auto Scaling (Opcional)**:
    - Se você espera flutuações de tráfego ou demandas de carga de trabalho, pode configurar políticas de auto scaling para ajustar automaticamente o número de tarefas no seu serviço com base na utilização de CPU/memória ou outras métricas.

#### Passo 4: Monitoramento e Escalabilidade

1. **Monitoramento com CloudWatch**:
    - Utilize o Amazon CloudWatch para monitorar o desempenho do seu cluster ECS, tarefas e serviços.
    - Configure alarmes do CloudWatch para notificá-lo sobre quaisquer problemas de desempenho ou restrições de recursos.

2. **Estratégias de Escalabilidade**:
    - O ECS fornece estratégias de escalabilidade para ajustar automaticamente seus serviços com base na demanda.
    - Você pode usar políticas de escalabilidade baseadas em meta para manter um nível de utilização de CPU ou memória, ou definir políticas de escalabilidade personalizadas com base em métricas específicas.

#### Exemplo de Implantação de Código

Aqui está um exemplo simplificado de implantação de uma aplicação containerizada usando ECS:

```yaml
version: '3'

services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
    deploy:
      replicas: 2
      restart_policy:
        condition: on-failure
```

Este arquivo Docker Compose define um serviço chamado "web" usando a imagem Docker do NGINX. Ele especifica que duas réplicas do container devem ser implantadas e expõe a porta 80 para tráfego web.

### Gerenciamento de Clusters, Tarefas e Serviços no ECS:

Isso envolve várias tarefas para garantir a operação suave e a utilização eficiente de recursos. Vamos detalhar cada aspecto:

1. **Gerenciamento de Clusters**:
    - **Escalabilidade da Capacidade do Cluster**:
        - O ECS permite escalar a capacidade do cluster adicionando ou removendo instâncias EC2 ou tarefas Fargate com base na demanda de carga de trabalho.
        - Você pode usar o AWS Auto Scaling para ajustar automaticamente o número de instâncias no cluster com base na utilização de CPU/memória ou outras métricas personalizadas.
    - **Monitoramento e Verificações de Saúde**:
        - Monitore a saúde e o desempenho do seu cluster ECS usando o Amazon CloudWatch.
        - Configure alarmes no CloudWatch para alertá-lo sobre quaisquer problemas, como instâncias se tornando insalubres ou atingindo limites de recursos.
    - **Otimização da Alocação de Recursos**:
        - Analise as métricas de utilização de recursos para otimizar a alocação de CPU, memória e recursos de rede em seu cluster.
        - Use os ECS Capacity Providers para gerenciar a alocação de tarefas em vários clusters e pools de instâncias spot, otimizando custos e utilização de recursos.

2. **Gerenciamento de Tarefas**:
    - **Ciclo de Vida da Tarefa**:
        - Visualize e gerencie tarefas individuais dentro do seu cluster ECS usando o console do ECS ou a AWS CLI.
        - Você pode parar, iniciar ou reiniciar tarefas manualmente, ou definir políticas de ciclo de vida para automatizar o gerenciamento de tarefas com base em critérios específicos.
    - **Estratégias de Colocação de Tarefas**:


- Defina restrições e estratégias de colocação de tarefas para controlar onde as tarefas são colocadas dentro do seu cluster.
  - Use restrições de colocação de tarefas para especificar atributos de instância ou atributos personalizados para colocação de tarefas, garantindo utilização e desempenho ideais de recursos.
    - **Agendamento de Tarefas**:
        - O ECS suporta agendamento de tarefas usando o Amazon ECS Task Scheduler ou agendadores de terceiros como Kubernetes ou Nomad.
        - Agende tarefas para rodar em horários ou intervalos específicos, ou em resposta a eventos ou gatilhos usando o AWS Lambda ou o Amazon EventBridge.

3. **Gerenciamento de Serviços**:
    - **Implantação de Serviços**:
        - Implemente e gerencie serviços dentro do seu cluster ECS para garantir que o número desejado de tarefas esteja sendo executado e acessível para os usuários.
        - Defina configurações de serviço, incluindo definições de tarefas, contagem desejada, tipo de implantação e configurações de balanceamento de carga.
    - **Atualizações Incrementais e Estratégias de Implantação**:
        - Realize atualizações incrementais e implantações para atualizar configurações de serviços ou implantar novas versões da sua aplicação sem interrupções.
        - Configure estratégias de implantação como atualizações incrementais ou implantações blue/green para minimizar o tempo de inatividade e garantir alta disponibilidade.
    - **Descoberta de Serviços e Balanceamento de Carga**:
        - Use o AWS Cloud Map para descoberta de serviços, permitindo que tarefas dentro do seu cluster ECS descubram e se comuniquem entre si usando DNS.
        - Configure o Elastic Load Balancing (ELB) ou Application Load Balancers (ALB) para distribuir o tráfego entre as tarefas dentro do seu serviço ECS.

### Perguntas de Entrevista Baseadas em Cenários:

1. Você percebe que a utilização de CPU do cluster ECS está consistentemente alta durante as horas de pico. Como você abordaria esse problema?
2. Uma nova aplicação requer configurações de hardware especializadas que não estão disponíveis no cluster ECS existente. Como você lidaria com essa situação?
3. Você precisa garantir que tarefas críticas estejam sempre em execução no cluster ECS, mesmo em caso de falhas de instância. Como você alcançaria alta disponibilidade para essas tarefas?
4. Você tem um trabalho de processamento em lote que precisa ser executado em um horário específico todos os dias. Como você agendaria essa tarefa no ECS?
5. Sua equipe está implantando uma nova versão de um microsserviço no cluster ECS. Como você realizaria uma atualização incremental para minimizar o tempo de inatividade?
6. Você precisa implementar descoberta de serviços para um conjunto de microsserviços em execução no cluster ECS. Como você abordaria essa tarefa?

### Conclusão:

O ECS simplifica a implantação e o gerenciamento de aplicações containerizadas na AWS. Ao compreender os princípios de conteinerização, as noções básicas do Docker e dominar o ECS, você pode otimizar seus processos de desenvolvimento e implantação, garantindo escalabilidade, confiabilidade e eficiência para suas aplicações.

Isso conclui o Dia 15 da nossa jornada pela AWS. Amanhã, exploraremos outro serviço fascinante da AWS. Fique ligado!
