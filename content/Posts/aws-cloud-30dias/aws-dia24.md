---
title: "Dia 24: Práticas de DevOps na AWS"
date: "2024-08-29"
description: "Essa é uma prática fundamental nos fluxos de trabalho modernos de desenvolvimento de software."
categories: ["Cloud"]
tags: ["AWS", "DevOps", "CloudFormation", "CodePipeline", "CodeDeploy", "CloudWatch"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia24"]
author: ["Edilson Freitas"]
cover:
  image: images/devops.png
  hiddenInList: true
---

## Bem-vindo ao Dia 24 do nosso abrangente curso de 30 dias sobre AWS! 

Hoje, mergulhamos no mundo das práticas de DevOps, focando na implementação de pipelines de Integração Contínua/Entrega Contínua (CI/CD) com o AWS CodePipeline e CodeDeploy. Além disso, vamos automatizar o provisionamento de infraestrutura usando CloudFormation e garantir o monitoramento eficiente e o registro de logs dos nossos fluxos de trabalho de DevOps com o CloudWatch.

### Implementando pipelines CI/CD com AWS CodePipeline e CodeDeploy

Essa é uma prática fundamental nos fluxos de trabalho modernos de desenvolvimento de software. Vamos explorar cada componente e como eles trabalham juntos para automatizar o processo de implantação:

#### AWS CodePipeline

O AWS CodePipeline é um serviço de integração contínua e entrega contínua totalmente gerenciado fornecido pela AWS. Ele automatiza as fases de build, teste e implantação do seu processo de release. Veja como ele funciona:

- **Estrutura do Pipeline:** Um pipeline do CodePipeline consiste em uma série de estágios, cada um representando uma etapa do seu processo de release. Cada estágio pode conter uma ou mais ações, como recuperação de código-fonte, build, teste e implantação.
- **Integração com Outros Serviços:** O CodePipeline integra-se perfeitamente a vários serviços da AWS, incluindo AWS CodeCommit (para repositórios de código-fonte), AWS CodeBuild (para construção de artefatos), AWS CodeDeploy (para implantação), entre outros. Ele também suporta integração com ferramentas de terceiros por meio de ações personalizadas.
- **Flexibilidade e Personalização:** Você pode personalizar seu pipeline para atender aos seus requisitos específicos. Por exemplo, você pode incluir ações de aprovação manual para controlar o fluxo de implantações ou usar recursos avançados como a execução paralela e sequencial de ações.

#### AWS CodeDeploy

O AWS CodeDeploy é um serviço de implantação que automatiza a implantação de aplicações em instâncias EC2, funções Lambda e outros serviços de computação. Ele permite que você faça implantações de forma confiável e consistente, reduzindo o tempo de inatividade e minimizando erros. Veja como ele funciona:

- **Configurações de Implantação:** O CodeDeploy permite que você defina configurações de implantação, que especificam como sua aplicação deve ser implantada. Você pode escolher entre diferentes estratégias de implantação, como implantações in-place, blue/green e canary.
- **Grupos de Implantação:** Você organiza seus alvos de implantação em grupos de implantação. Esses grupos podem incluir instâncias EC2, funções Lambda ou até mesmo servidores on-premises. Você pode definir regras de implantação e hooks de ciclo de vida para cada grupo de implantação, controlando o processo de implantação.
- **Mecanismo de Rollback:** O CodeDeploy fornece um mecanismo de rollback embutido que reverte automaticamente para a versão anterior da sua aplicação se uma implantação falhar ou se disparar alarmes com base em verificações de integridade.

**Integração do CodePipeline com o CodeDeploy:**

- **Estágio de Fonte:** O CodePipeline busca o código-fonte do repositório escolhido, como AWS CodeCommit ou GitHub.
- **Estágio de Build:** O código-fonte é então construído em artefatos implantáveis usando o AWS CodeBuild ou qualquer outro serviço de build de sua escolha.
- **Estágio de Teste:** Testes automatizados podem ser executados para garantir a qualidade e a estabilidade da aplicação.
- **Estágio de Implantação:** Uma vez que os artefatos passam nos testes, o CodePipeline aciona o CodeDeploy para implantar os artefatos nos alvos de implantação especificados (por exemplo, instâncias EC2).
- **Ações Pós-Implantação:** O CodePipeline pode executar ações pós-implantação, como executar testes adicionais ou atualizar a documentação.

### Automatizando o provisionamento de infraestrutura com o CloudFormation

O CloudFormation permite que você defina e implemente recursos da AWS de forma declarativa usando um arquivo de template. Aqui está uma visão abrangente de como o CloudFormation funciona e seus benefícios:

#### Templates do CloudFormation

- **Templates do CloudFormation são arquivos JSON ou YAML** que descrevem os recursos da AWS e suas configurações.
- **Definição Declarativa:** Os templates fornecem uma maneira declarativa de definir sua infraestrutura. Em vez de scriptar os passos para criar recursos, você declara o estado desejado da sua infraestrutura.
- **Parametrização:** O CloudFormation permite que você parametrize seus templates, habilitando a personalização dinâmica durante a criação da stack.
- **Tipos de Recursos:** O CloudFormation suporta uma ampla gama de tipos de recursos da AWS, incluindo computação, armazenamento, redes, banco de dados, segurança, e muito mais.
- **Gerenciamento de Stacks:** No CloudFormation, uma stack é uma coleção de recursos da AWS criada e gerenciada como uma unidade única. Você pode criar, atualizar e deletar stacks usando o Console de Gerenciamento da AWS, CLI ou SDKs.
- **Change Sets:** Antes de fazer mudanças em uma stack, o CloudFormation permite que você visualize as mudanças usando um Change Set.
- **Integração com Outros Serviços da AWS:** O CloudFormation se integra perfeitamente a outros serviços da AWS, permitindo que você provisione arquiteturas complexas e automatize fluxos de trabalho de implantação.

### Monitorando e registrando logs dos fluxos de trabalho DevOps com CloudWatch

O CloudWatch oferece um conjunto abrangente de serviços de monitoramento e logging adaptados para atender às necessidades das equipes DevOps. Vamos explorar como o CloudWatch facilita o monitoramento e o registro de logs em vários aspectos dos seus recursos e aplicações AWS:

#### Métricas e Alarmes

- **O CloudWatch coleta e armazena métricas** de serviços da AWS, incluindo EC2, Lambda, S3, RDS, e muitos outros.
- **Logs e Grupos de Logs:** O CloudWatch Logs permite que você centralize a coleta e o armazenamento de logs gerados por suas aplicações, sistemas operacionais e serviços AWS.
- **Integração com Serviços da AWS:** O CloudWatch se integra perfeitamente com vários serviços da AWS, permitindo que você monitore e analise seu desempenho e integridade.
- **Métricas e Logs Personalizados:** Além de monitorar serviços da AWS, o CloudWatch permite que você publique métricas e logs personalizados das suas aplicações.
- **Dashboards e Visualização:** Os Dashboards do CloudWatch fornecem visualizações em tempo real personalizáveis de suas métricas e logs.

### Exemplos de Implementação

Aqui estão exemplos que demonstram a implementação de vários conceitos discutidos anteriormente usando serviços da AWS, como CloudFormation, CodePipeline, CodeDeploy e CloudWatch.

**Exemplo de Template do CloudFormation:**

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Description: Example CloudFormation Template

Parameters:
  InstanceType:
    Type: String
    Default: t2.micro
    Description: EC2 instance type

Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: !Ref InstanceType
      ImageId: ami-0c55b159cbfafe1f0
      SecurityGroups:
        - Ref: MySecurityGroup

Outputs:
  InstanceId:
    Description: Instance ID
    Value: !Ref MyEC2Instance
    Export:
      Name: MyEC2InstanceId
```

**Exemplo de Configuração do AWS CodePipeline:**

```json
{
  "pipeline": {
    "name": "MyPipeline",
    "roleArn": "arn:aws:iam::123456789012:role/service-role/AWS-CodePipeline-Service",
    "artifactStore": {
      "type": "S3",
      "location": "my-bucket"
    },
    "stages": [
      {
        "name": "Source",
        "actions": [
          {
            "name": "SourceAction",
            "actionTypeId": {
              "category": "Source",
              "owner": "AWS",
              "provider": "CodeCommit",
              "version": "1"
            },
            "configuration": {
              "RepositoryName": "MyRepo",
              "BranchName": "main"
            },
            "outputArtifacts": [
              {
                "name": "SourceOutput"
              }
            ],
            "runOrder": 1
          }
        ]
      },
      {
        "name": "Build",
        "actions": [
          {
            "name": "BuildAction",
            "actionTypeId": {
              "category": "Build",
              "owner": "AWS",
              "provider": "CodeBuild",
              "version": "1"
            },
            "inputArtifacts": [
              {
                "name": "SourceOutput"
              }
            ],
            "configuration": {
              "ProjectName": "MyCodeBuildProject"
            },
            "runOrder": 1
          }
        ]
      },
      {
        "name": "Deploy",
        "actions": [
          {
            "name": "DeployAction",
            "actionTypeId": {
              "category": "Deploy",
              "owner": "AWS",
              "provider": "CodeDeploy",
              "version": "1"
            },
            "inputArtifacts": [
              {
                "name": "SourceOutput"
              }
            ],
            "configuration": {
              "ApplicationName": "MyApplication",
              "DeploymentGroupName": "MyDeploymentGroup"
            },
            "runOrder": 1


          }
        ]
      }
    ]
  }
}
```

**Exemplo de Alarme do CloudWatch:**

```json
{
  "AlarmName": "HighCPUUtilization",
  "AlarmDescription": "Alarm triggered when CPU utilization exceeds 80%",
  "ActionsEnabled": true,
  "AlarmActions": ["arn:aws:sns:us-east-1:123456789012:MyTopic"],
  "MetricName": "CPUUtilization",
  "Namespace": "AWS/EC2",
  "Statistic": "Average",
  "Dimensions": [
    {
      "Name": "InstanceId",
      "Value": "i-1234567890abcdef0"
    }
  ],
  "Period": 300,
  "EvaluationPeriods": 1,
  "Threshold": 80,
  "ComparisonOperator": "GreaterThanOrEqualToThreshold",
  "TreatMissingData": "notBreaching",
  "Unit": "Percent"
}
```

### Perguntas de Entrevista Baseadas em Cenários

Aqui estão perguntas de entrevista baseadas em cenários focando nos tópicos de CloudFormation, CodePipeline, CodeDeploy e CloudWatch:

1. **Sua equipe está planejando implantar uma nova aplicação na AWS, e você foi encarregado de configurar a infraestrutura usando CloudFormation. Você pode nos guiar pelos passos que tomaria para atingir esse objetivo?**
2. **Você herdou um template CloudFormation de um projeto anterior e precisa fazer algumas modificações nele. Como você abordaria a revisão e a atualização do template existente?**
3. **Sua equipe está adotando uma abordagem CI/CD para entrega de software, e você foi encarregado de configurar um CodePipeline para automatizar o processo de implantação. Você pode descrever os passos envolvidos na configuração de um CodePipeline para esse propósito?**
4. **Sua equipe está enfrentando falhas frequentes no pipeline durante as implantações, impactando o ciclo de lançamento de software. Como você solucionaria e resolveria esses problemas?**
5. **Sua equipe está planejando implantar uma nova versão da aplicação em produção usando o AWS CodeDeploy. Você pode descrever o processo de implantação e as melhores práticas que seguiria?**
6. **Sua equipe está enfrentando falhas de implantação com o AWS CodeDeploy devido a instâncias que não conseguem baixar os artefatos de implantação. Como você solucionaria e resolveria esse problema?**

### Conclusão

Hoje, exploramos as principais práticas de DevOps na AWS, incluindo a implementação de pipelines CI/CD com CodePipeline e CodeDeploy, automação do provisionamento de infraestrutura com CloudFormation e monitoramento dos fluxos de trabalho DevOps com CloudWatch.

Fique atento para mais insights enquanto continuamos nossa jornada pelo ecossistema da AWS!