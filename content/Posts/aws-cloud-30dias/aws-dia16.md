---
title: "Dia 16: Amazon EKS (Elastic Kubernetes Service)"
date: "2024-08-21"
description: "O Kubernetes revolucionou a maneira como implantamos, gerenciamos e escalamos aplicações containerizadas."
categories: ["Cloud"]
tags: ["EKS", "docker", "container", "kubernetes"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia16"]
author: ["Edilson Freitas"]
cover:
  image: images/eks.jpg
  hiddenInList: true
---

## Bem-vindo de volta à nossa jornada de 30 dias pela AWS! 

Hoje, no Dia 16, mergulharemos profundamente no mundo poderoso do Elastic Kubernetes Service (EKS) na AWS. 

`O Kubernetes revolucionou a maneira como implantamos, gerenciamos e escalamos aplicações containerizadas, e com o EKS, a AWS oferece uma experiência Kubernetes gerenciada e integrada.`

Confira as perguntas de entrevista baseadas em cenários no final deste blog. Se precisar de respostas para essas perguntas, não hesite em nos contatar pelos comentários!

### Introdução ao Kubernetes e EKS:

Vamos aprofundar na introdução ao Kubernetes e ao Elastic Kubernetes Service (EKS).

#### Introdução ao Kubernetes:

O Kubernetes, comumente referido como K8s (devido às oito letras entre 'K' e 's'), é uma plataforma de orquestração de containers open-source desenvolvida inicialmente pelo Google. Ele oferece uma solução poderosa para automatizar a implantação, escalabilidade e gerenciamento de aplicações containerizadas.

**Conceitos Básicos do Kubernetes:**

1. **Pods:** A menor unidade implantável no Kubernetes, representando um ou mais containers que compartilham recursos de rede e armazenamento.

2. **Implantações:** Um recurso de alto nível no Kubernetes que gerencia a implantação e escalabilidade de pods. Ele permite atualizações declarativas das aplicações, facilitando o gerenciamento e a escalabilidade.

3. **Serviços:** Uma abstração que define um conjunto de pods e uma política para acessá-los. Os serviços permitem a exposição de aplicações executadas no Kubernetes para outros aplicativos ou usuários.

4. **Nós:** São os servidores individuais que executam pods. Os nós podem ser máquinas virtuais ou físicas.

5. **Kubernetes Master:** O plano de controle que gerencia o cluster Kubernetes, incluindo a escalabilidade das aplicações e o gerenciamento de falhas de nós.

6. **Kubelet:** Um agente que roda em cada nó do cluster, responsável por garantir que os containers estejam em execução dentro de um pod.

7. **kubectl:** A interface de linha de comando (CLI) usada para interagir com os clusters Kubernetes. Ela permite aos usuários criar, modificar e gerenciar recursos do Kubernetes.

#### Introdução ao Elastic Kubernetes Service (EKS):

O Elastic Kubernetes Service (EKS) é o serviço gerenciado de Kubernetes da Amazon Web Services (AWS). Ele simplifica o processo de implantação, gerenciamento e escalabilidade de clusters Kubernetes na infraestrutura da AWS.

**Principais Características do Amazon EKS:**

1. **Plano de Controle Totalmente Gerenciado:** O EKS elimina a necessidade de os usuários gerenciarem o plano de controle do Kubernetes. A AWS cuida de tarefas como aplicação de patches, atualizações e escalabilidade do plano de controle para alta disponibilidade.

2. **Integração com Serviços da AWS:** O EKS se integra perfeitamente com outros serviços da AWS, como Elastic Load Balancing, Identity and Access Management (IAM), CloudWatch e AWS Fargate, facilitando a construção e operação de aplicações no Kubernetes.

3. **Segurança e Conformidade:** O EKS oferece recursos de segurança integrados, incluindo autenticação IAM para clusters Kubernetes, isolamento de rede usando Amazon VPC e integração com o AWS Key Management Service (KMS) para criptografia em repouso.

4. **Escalabilidade e Disponibilidade:** O EKS escala automaticamente o plano de controle do Kubernetes com base na carga de trabalho e garante alta disponibilidade ao distribuí-lo por várias zonas de disponibilidade.

5. **Compatibilidade e Abertura:** O EKS é certificado como compatível com o Kubernetes, garantindo compatibilidade com ferramentas e aplicações existentes no Kubernetes. Ele suporta APIs Kubernetes open-source, permitindo a migração sem interrupções de cargas de trabalho existentes para o EKS.

Ao aproveitar o Elastic Kubernetes Service (EKS), os usuários podem se concentrar mais na construção e implantação de aplicações, enquanto a AWS gerencia a infraestrutura subjacente e o plano de controle do Kubernetes, acelerando o ciclo de desenvolvimento e melhorando a eficiência operacional.

### Implantando Clusters Kubernetes com EKS:

Isso envolve várias etapas para provisionar o cluster e configurá-lo para suas aplicações. Vamos detalhar o processo:

**Implantando Clusters Kubernetes com EKS:**

1. **Pré-requisitos:**

    - **Conta AWS:** Certifique-se de ter acesso a uma conta AWS com as permissões necessárias para criar clusters EKS.
    - **AWS CLI:** Instale e configure a Interface de Linha de Comando da AWS (CLI) em sua máquina local.
    - **Função IAM:** Crie uma função IAM com permissões para o EKS. Essa função será usada pelo EKS para gerenciar recursos em seu nome.
    - **VPC e Sub-redes:** Crie uma Virtual Private Cloud (VPC) com pelo menos duas sub-redes em diferentes Zonas de Disponibilidade.

2. **Criar um Cluster Amazon EKS:**

   Use o Console de Gerenciamento da AWS ou a AWS CLI para criar um cluster EKS. Você precisará especificar parâmetros como o nome do cluster, versão do Kubernetes, VPC, sub-redes e função IAM.

   Exemplo de comando CLI:
    ```sh
    aws eks create-cluster --name <cluster-name> --role-arn <role-arn> --resources-vpc-config subnetIds=<subnet-1>,<subnet-2>,securityGroupIds=<security-group-id>
    ```

3. **Configurar kubectl:**

   Após a criação do cluster, configure a ferramenta de linha de comando do Kubernetes, o kubectl, para se comunicar com o cluster EKS.

   Execute o seguinte comando da AWS CLI para atualizar seu arquivo kubeconfig:
    ```sh
    aws eks --region <region> update-kubeconfig --name <cluster-name>
    ```

4. **Verificar o Cluster:**

   Use o kubectl para verificar o status do cluster e as informações dos nós:
    ```sh
    kubectl get nodes
    ```

5. **Add-ons Opcionais:**

   Configure add-ons adicionais como o AWS Load Balancer Controller, AWS App Mesh ou Amazon CloudWatch Container Insights para aprimorar as capacidades do seu cluster EKS.

6. **Controle de Acesso:**

   Implemente funções IAM para contas de serviço (IRSA) ou o controle de acesso baseado em funções do Kubernetes (RBAC) para gerenciar o acesso aos recursos dentro do cluster.

7. **Configuração de Rede:**

   Configure componentes de rede como plugins CNI (Container Network Interface) para VPC, controladores de ingresso e controles de tráfego de saída para garantir a comunicação adequada dentro e fora do cluster.

8. **Grupos de Nós (Opcional):**

   Crie um ou mais grupos de nós para lançar nós de trabalho dentro do cluster EKS. Os grupos de nós permitem que você especifique tipos de instância, pares de chaves do Amazon EC2 e configurações de escalabilidade.

9. **Grupos de Nós Gerenciados (Opcional):**

   Alternativamente, você pode criar grupos de nós gerenciados, que são totalmente gerenciados pela AWS e provisionados automaticamente com base nas demandas da carga de trabalho.

10. **Monitoramento e Log:**

    Habilite o monitoramento e logging usando serviços da AWS como CloudWatch e AWS CloudTrail para rastrear o desempenho do cluster, saúde e atividade da API.

11. **Práticas de Segurança:**

    Implemente práticas recomendadas de segurança, como criptografia em repouso e em trânsito, segmentação de rede e auditorias regulares para garantir a segurança do seu cluster EKS e das aplicações.

Seguindo esses passos, você poderá implantar com sucesso um cluster Kubernetes com o Elastic Kubernetes Service (EKS) na AWS. O EKS simplifica o processo de gerenciamento da infraestrutura Kubernetes, permitindo que você se concentre na implantação e escalabilidade das suas aplicações containerizadas.

### Gerenciando e Escalando Aplicações Containerizadas com EKS:

Isso envolve aproveitar os recursos poderosos do Kubernetes para implantação, escalabilidade e gerenciamento. Vamos explorar os principais aspectos:

**Gerenciando Aplicações Containerizadas com EKS:**

1. **Implantando Aplicações:**

    - Defina a implantação de sua aplicação usando manifestos Kubernetes ou gráficos Helm. Essas configurações especificam detalhes como imagens de containers, requisitos de recursos, variáveis de ambiente e configurações de rede.
    - Aplique as configurações de implantação usando kubectl ou Helm para implantar suas aplicações no cluster EKS.

   Exemplo de YAML de Implantação:
    ```yaml
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: nginx-deployment
    spec:
      replicas: 3
      selector:
        matchLabels:
          app: nginx
      template:
        metadata:
          labels:
            app: nginx
        spec:
          containers:
          - name: nginx
            image: nginx:latest
            ports:
            - containerPort: 80
    ```

2. **Descoberta de Serviços e Balanceamento de Carga:**

    - Use Serviços do Kubernetes para expor suas aplicações internamente ou externamente. Os serviços fornecem um endpoint estável para acessar os pods da sua aplicação, independentemente dos seus endereços IP subjacentes.
    - Opcionalmente, configure o Elastic Load Balancing (ELB) ou Application Load Balancer (ALB) da AWS para distribuir o tráfego para seus pods de aplicação através de múltiplas Zonas de Disponibilidade.

**Escalando Aplicações Containerizadas com EKS:**

1

. **Horizontal Pod Autoscaler (HPA):**

    - O Horizontal Pod Autoscaler do Kubernetes ajusta automaticamente o número de pods réplicas em uma implantação com base na utilização observada de CPU ou métricas personalizadas.
    - Defina políticas de escalabilidade usando comandos kubectl ou manifestos YAML para escalar seus pods de aplicação horizontalmente.

    Exemplo de Configuração HPA:
    ```sh
    kubectl autoscale deployment nginx-deployment --cpu-percent=50 --min=1 --max=10
    ```

2. **Cluster Autoscaler:**

    - O EKS integra-se com o Cluster Autoscaler, um componente do Kubernetes que ajusta automaticamente o tamanho dos grupos de nós do seu cluster EKS com base nas necessidades de agendamento dos pods.
    - Configure o Cluster Autoscaler para monitorar solicitações de pods pendentes e escalar os grupos de nós para cima ou para baixo conforme necessário para garantir a utilização ideal dos recursos.

3. **Vertical Pod Autoscaler (VPA) (Opcional):**

    - O Vertical Pod Autoscaler ajusta as solicitações e limites de recursos dos pods com base nos padrões de uso de recursos.
    - Implemente o VPA para otimizar a alocação de recursos e melhorar a eficiência das suas aplicações containerizadas executadas no EKS.

4. **Métricas Personalizadas e Políticas de Escalabilidade:**

    - Utilize as APIs de Métricas Personalizadas do Kubernetes e Provedores de Métricas Externas para definir políticas de escalabilidade personalizadas com base em métricas específicas da aplicação, como latência de solicitação, tamanho de fila ou KPIs de negócios.
    - Integre com o AWS CloudWatch, Prometheus ou soluções de monitoramento de terceiros para coletar e expor métricas personalizadas para fins de escalabilidade automática.

**Monitoramento e Log:**

1. **Integração com o AWS CloudWatch:**

    - Utilize o AWS CloudWatch Container Insights para monitorar clusters EKS, aplicações containerizadas e a infraestrutura subjacente.
    - Colete e analise métricas, logs e eventos gerados por recursos EKS para obter insights sobre o desempenho, saúde e utilização de recursos do cluster.

2. **Integração com Prometheus e Grafana:**

    - Implemente Prometheus e Grafana para coletar, armazenar e visualizar métricas e logs do Kubernetes e das aplicações.
    - Configure exportadores do Prometheus e painéis do Grafana para monitorar clusters EKS, nós, pods e serviços em tempo real.

### Perguntas de Entrevista Baseadas em Cenários:

1. Você tem uma aplicação baseada em microsserviços composta por vários containers Docker que precisam ser implantados em um cluster EKS. Como você abordaria a implantação e o gerenciamento desses containers de forma eficaz?
3. Seu cluster EKS está enfrentando restrições de recursos devido ao aumento das demandas de carga de trabalho. Como você escalaria a infraestrutura subjacente para acomodar o número crescente de pods?
4. Sua aplicação requer configurações de hardware especializadas, e você precisa escalar os pods individualmente com base nos padrões de uso de recursos. Como você implementaria a escalabilidade vertical para sua aplicação no EKS?
5. Você precisa monitorar o desempenho e a saúde do seu cluster EKS e das aplicações containerizadas em execução nele. Como você configuraria o monitoramento e o log para sua infraestrutura EKS?
6. Sua equipe está implantando um novo microsserviço no cluster EKS, e você precisa garantir que o serviço seja altamente disponível e tolerante a falhas. Como você desenharia a arquitetura de implantação para atender a esses requisitos?
7. A carga de trabalho da sua aplicação exibe picos periódicos de tráfego, exigindo escalabilidade dinâmica dos recursos para lidar com a demanda aumentada. Como você implementaria estratégias proativas de escalabilidade para antecipar e responder eficazmente às flutuações de tráfego?
8. Sua equipe precisa garantir conformidade com requisitos regulatórios mantendo logs de auditoria abrangentes para todas as ações realizadas no cluster EKS. Como você implementaria mecanismos de auditoria e log para atender a esses requisitos de conformidade?

Isso conclui o Dia 16 da nossa jornada pelo curso da AWS, onde exploramos o Elastic Kubernetes Service (EKS) e suas capacidades na implantação, gerenciamento e escalabilidade de aplicações containerizadas. Fique atento para mais conteúdo empolgante nos próximos dias!