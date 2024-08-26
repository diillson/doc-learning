---
title: "Dia 22: Arquitetura Serverless"
date: "2024-08-27"
description: "A arquitetura serverless abstrai a infraestrutura subjacente, permitindo que os desenvolvedores se concentrem apenas na escrita de código."
categories: ["Cloud"]
tags: ["AWS", "AWSServeless", "lambda", "APIGateway"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia22"]
author: ["Edilson Freitas"]
cover:
  image: images/serveless.png
  hiddenInList: true
---

## Bem-vindo de volta à nossa jornada de 30 dias no curso da AWS! 

Hoje, vamos nos aprofundar no mundo da arquitetura serverless, uma mudança de paradigma em como construímos e implantamos aplicações. Neste post, exploraremos os componentes centrais do serverless na AWS, incluindo Lambda, API Gateway, SNS e SQS. Vamos começar!

### Compreendendo a Arquitetura Serverless

Tradicionalmente, implantar e gerenciar servidores poderia ser uma tarefa árdua, exigindo manutenção constante e esforços de escalabilidade. A arquitetura serverless abstrai a infraestrutura subjacente, permitindo que os desenvolvedores se concentrem apenas na escrita de código. A AWS oferece um conjunto de serviços para facilitar o desenvolvimento de aplicações serverless, com o AWS Lambda e o API Gateway à frente.

#### 1. Entendendo o AWS Lambda:

O AWS Lambda permite que você execute código sem provisionar ou gerenciar servidores. Veja como você pode projetar aplicações serverless com Lambda:

- **Decomposição de Funções:** Divida sua aplicação em pequenas funções focadas que realizam tarefas específicas. Cada função deve fazer uma coisa e fazer bem, seguindo os princípios da arquitetura de microsserviços.
- **Execução Orientada por Eventos:** Funções Lambda são acionadas por vários eventos, como solicitações HTTP, uploads de objetos no S3, notificações SNS, etc. Projete suas funções para responder a esses eventos adequadamente. Por exemplo, você pode ter uma função Lambda que processa solicitações HTTP recebidas do API Gateway.
- **Execução Sem Estado:** As funções Lambda são stateless, o que significa que elas não mantêm estado entre as invocações. Projete suas funções para serem idempotentes e gerencie todo o estado necessário externamente, como usando bancos de dados como o DynamoDB ou armazenando estado no S3.
- **Código Otimizado:** Mantenha suas funções Lambda leves e eficientes para minimizar o tempo de execução e reduzir custos. Otimize dependências, use as melhores práticas específicas da linguagem e considere os tempos de cold start ao projetar suas funções.

#### 2. Utilizando o API Gateway:

O API Gateway complementa o Lambda fornecendo um serviço totalmente gerenciado para criar, implantar e gerenciar APIs. Veja como você pode projetar aplicações serverless com o API Gateway:

- **Design RESTful de API:** Defina os endpoints e recursos da sua API usando princípios RESTful. Mapeie cada endpoint para uma função Lambda correspondente ou integre com outros serviços AWS conforme necessário.
- **Transformação de Solicitações e Respostas:** O API Gateway permite que você transforme solicitações recebidas e respostas enviadas usando templates de mapeamento. Projete esses templates para converter formatos de dados, realizar validações e enriquecer solicitações/respostas com informações adicionais.
- **Segurança e Autenticação:** Implemente medidas de segurança, como autenticação e autorização, usando recursos do API Gateway, como chaves de API, autorizadores Lambda ou integração com AWS Cognito. Projete seus mecanismos de segurança para proteger suas APIs contra acessos não autorizados.
- **Limitação de Taxa e Throttling:** Evite abusos e controle o tráfego para suas APIs configurando limites de taxa e throttling no API Gateway. Projete esses limites com base nos padrões de tráfego esperados e nas restrições de recursos da sua aplicação.

**Cenário de Exemplo:**

Suponha que você esteja construindo uma aplicação serverless para uma plataforma de e-commerce. Você pode projetá-la da seguinte forma:

- **Funções Lambda:**
    - Função para lidar com autenticação de usuários.
    - Função para processar pedidos e atualizar o estoque.
    - Função para gerar faturas e enviar notificações por e-mail.
    - Função para recuperar informações de produtos.
- **API Gateway:**
    - Defina endpoints RESTful para autenticação de usuários, processamento de pedidos e recuperação de produtos.
    - Configure transformações de solicitações/respostas para validação de dados e formatação.
    - Implemente medidas de segurança, como chaves de API e autorizadores Lambda, para proteger os endpoints da API.
    - Configure limites de taxa e throttling para gerenciar o tráfego de entrada de forma eficaz.

### Implementando Arquiteturas Orientadas por Eventos com SNS e SQS

Isso permite que você construa sistemas desacoplados, escaláveis e resilientes na AWS. Vamos explorar os conceitos-chave e como utilizar efetivamente o SNS e SQS em suas aplicações serverless:

#### 1. Entendendo o SNS e o SQS:

- **SNS (Simple Notification Service):** O SNS é um serviço de mensagens pub/sub totalmente gerenciado que permite desacoplar os publicadores de mensagens dos assinantes. Os publicadores podem enviar mensagens para tópicos, e os assinantes podem receber mensagens desses tópicos via vários protocolos, como HTTP, e-mail, SMS, Lambda, SQS, etc.
- **SQS (Simple Queue Service):** O SQS é um serviço de filas de mensagens totalmente gerenciado que oferece filas de mensagens escaláveis, distribuídas e confiáveis. As mensagens são enviadas para filas pelos produtores e recuperadas pelos consumidores. O SQS garante que as mensagens sejam entregues exatamente uma vez e na mesma ordem em que foram enviadas.

**Padrões de Design para Arquiteturas Orientadas por Eventos:**

- **Padrão Fan-Out:** Use o SNS para disseminar mensagens para várias filas SQS ou funções Lambda. Este padrão é útil para cenários em que vários componentes precisam processar o mesmo evento de forma independente.
- **Invocações Encadeadas:** Encadeie funções Lambda usando SNS e SQS. A saída de uma função Lambda pode acionar outra função publicando uma mensagem em uma fila SQS ou tópico SNS, possibilitando fluxos de trabalho complexos.
- **Dead Letter Queue (DLQ):** Configure filas SQS com uma DLQ para lidar com mensagens que não puderam ser processadas com sucesso após um certo número de tentativas. Isso ajuda a identificar e depurar falhas de processamento.

**Cenário de Exemplo:**

Vamos considerar uma plataforma de mídia social onde os usuários podem fazer upload de imagens. Você pode implementar uma arquitetura orientada por eventos para lidar com processamento de imagens e notificações da seguinte forma:

- **Evento de Upload de Imagem:** Quando um usuário faz upload de uma imagem, a aplicação publica uma mensagem em um tópico SNS chamado "ImageUploadTopic".
- **Processamento de Imagem:** Várias funções Lambda se inscrevem no "ImageUploadTopic" para processar as imagens enviadas. Uma função Lambda redimensiona a imagem para gerar miniaturas, outra aplica filtros, e uma terceira extrai metadados.
- **Notificação:** Assim que o processamento da imagem estiver concluído, outra função Lambda publica uma mensagem em um tópico SNS chamado "ImageProcessedTopic", indicando que o processamento da imagem foi concluído.
- **Notificação ao Usuário:** Assinantes, como serviços de notificação por e-mail ou push, inscrevem-se no "ImageProcessedTopic" para notificar os usuários de que suas imagens foram processadas e estão prontas para visualização.

**Benefícios das Arquiteturas Orientadas por Eventos:**

- **Escalabilidade:** SNS e SQS podem lidar com grandes volumes de mensagens e escalar automaticamente para acomodar cargas de trabalho variáveis.
- **Resiliência:** Desacoplar componentes com SNS e SQS aumenta a tolerância a falhas e a resiliência. Se um componente falhar, isso não afeta o sistema como um todo.
- **Flexibilidade:** Arquiteturas orientadas por eventos permitem adicionar ou remover componentes facilmente sem impactar outras partes do sistema.

### Escalando e Monitorando Aplicações Serverless

Vamos explorar como você pode escalar e monitorar suas aplicações serverless de forma eficaz na AWS:

#### Escalando Aplicações Serverless:

1. **Auto Scaling:**

- **AWS Lambda:** O Lambda escala automaticamente para lidar com o aumento de tráfego de entrada. Cada função pode escalar de forma independente, permitindo que você otimize a alocação de recursos com base nas demandas de carga de trabalho.
- **API Gateway:** O API Gateway escala automaticamente para acomodar taxas de solicitação variáveis. Você pode configurar as definições de escalabilidade com base em fatores como o número de solicitações ou taxas de erro.

2. **Execuções Concorrentes:**

- **AWS Lambda:** Monitore execuções concorrentes de funções Lambda usando métricas do CloudWatch. Ajuste as configurações de concorrência reservada e provisionada para garantir desempenho ideal durante picos de tráfego.
- **API Gateway:** Monitore conexões e solicitações concorrentes nos endpoints do API Gateway. Ajuste as definições de throttling para lidar com aumentos repentinos no tráfego de forma tranquila.

3. **Capacidade Provisionada do DynamoDB:**

- Se sua aplicação serverless depende do DynamoDB, considere provisionar capacidade para lidar com cargas de trabalho antecipadas. Use Auto Scaling para o DynamoDB para ajustar a capacidade com base nos padrões de uso real.

4. **Otimização de Cold Start:**

- Minimize os tempos de cold start para funções Lambda otimizando o código, reduzindo tamanhos de pacotes e aproveitando a concorrência provisionada. Isso garante que as funções possam responder rapidamente a solicitações de entrada, especialmente durante picos súbitos de tráfego.

#### Monitorando Aplicações Serverless:

1. **Métricas do CloudWatch:**

- **AWS Lambda:** Monitore métricas-chave como contagem de invocações, duração e erros usando métricas do CloudWatch. Configure alarmes para alertá-lo quando os limites forem excedidos.
- **API Gateway:** Monitore métricas como latência, erros de integração e códigos de status 5XX para identificar problemas de desempenho. Use logs do CloudWatch para capturar informações detalhadas de solicitações/respostas.

2. **Rastreamento Distribuído:**

- Implemente rastreamento distribuído usando o AWS X-Ray para obter insights sobre o desempenho de ponta a ponta das aplicações serverless. Rastreie solicitações à medida que elas passam por funções Lambda, API Gateway e outros serviços da AWS.

3. **Agregação de Logs:**

- Agregue logs de funções Lambda e do API Gateway usando o CloudWatch Logs. Centralize os dados de log para facilitar a resolução de problemas e a análise. Configure políticas de retenção de logs para gerenciar os custos de armazenamento de forma eficaz.

4. **Métricas Personalizadas:**

- Crie métricas personalizadas no CloudWatch para rastrear indicadores de desempenho específicos da aplicação. Monitore métricas de negócios, como inscrições de usuários ou transações processadas, para avaliar a saúde geral da sua aplicação serverless.

5. **Monitoramento de Custos:**

- Use o AWS Cost Explorer para monitorar o custo de execução das aplicações serverless. Analise as tendências de custos, identifique os principais drivers de custo e otimize o uso de recursos para minimizar despesas.

**Cenário de Exemplo:**

Suponha que você tenha uma aplicação de e-commerce serverless construída no AWS Lambda e no API Gateway. Para escalar e monitorar essa aplicação de forma eficaz:

- **Auto Scaling:** Configure funções Lambda e endpoints do API Gateway para escalar automaticamente com base no tráfego de entrada.
- **Métricas do CloudWatch:** Monitore a contagem de invocações, duração e erros do Lambda. Acompanhe a latência e taxas de erro do API Gateway.
- **Rastreamento Distribuído:** Implemente o X-Ray para rastrear solicitações do API Gateway pelas funções Lambda até o DynamoDB.
- **Agregação de Logs:** Agregue logs de funções Lambda e do API Gateway no CloudWatch Logs para monitoramento e análise centralizada.
- **Métricas Personalizadas:** Crie métricas personalizadas no CloudWatch para monitorar pedidos processados, registros de usuários e outras métricas de negócios.
- **Monitoramento de Custos:** Use o Cost Explorer para monitorar os custos de invocações do Lambda, solicitações do API Gateway e outros recursos da AWS utilizados pela aplicação.

### Exemplo de Código

Vamos fornecer trechos de código de exemplo cobrindo os vários aspectos de escalabilidade e monitoramento de aplicações serverless usando AWS Lambda e API Gateway.

1. **Auto Scaling de Funções Lambda:**

```python
# Exemplo de código de função Lambda
import json
import time

def lambda_handler(event, context):
    time.sleep(5)  # Simula carga de trabalho
    return {
        'statusCode': 200,
        'body': json.dumps('Olá do Lambda!')
    }
```

2. **Monitoramento de Métricas do Lambda:**

```python
import boto3

# Cria cliente do CloudWatch
cloudwatch = boto3.client('cloudwatch')

def lambda_handler(event, context):
    # Envia métrica personalizada para o CloudWatch
    cloudwatch.put_metric_data(
        Namespace='MetricasPersonalizadas',
        MetricData=[
            {
                'MetricName': 'MetricaPersonalizada',
                'Value': 1,
                'Unit': 'Count'
            }
        ]
    )
    return {
        'statusCode': 200,
        'body': json.dumps('Métrica enviada para o CloudWatch')
    }
```

3. **Auto Scaling do API Gateway:**

```yaml
# Exemplo de template do API Gateway (Swagger/OpenAPI)
swagger: '2.0'
info:
  title: 'API de Exemplo'
  version: '1.0'
basePath: '/prod'
schemes:
  - 'https'
paths:
  /hello:
    get:
      responses:
        '200':
          description: 'Sucesso'
      x-amazon-apigateway-integration:
        uri: 'arn:aws:apigateway:us-east-1:lambda:path/2015-03-31/functions/arn:aws:lambda:us-east-1:123456789012:function:hello/invocations'
        httpMethod: 'POST'
        type: 'aws_proxy'
        connectionType: 'INTERNET'
        contentHandling: 'CONVERT_TO_TEXT'
```

4. **Monitoramento de Métricas do API Gateway:**

```python
import boto3

# Cria cliente do CloudWatch
cloudwatch = boto3.client('cloudwatch')

def lambda_handler(event, context):
    # Envia métrica personalizada para o CloudWatch
    cloudwatch.put_metric_data(
        Namespace='MetricasAPIGateway',
        MetricData=[
            {
                'MetricName': 'ContagemSolicitacoes',
                'Value': 1,
                'Unit': 'Count',
                'Dimensions': [
                    {
                        'Name': 'NomeAPI',
                        'Value': 'APIExemplo'
                    }
                ]
            }
        ]
    )
    return {
        'statusCode': 200,
        'body': json.dumps('Métrica enviada para o CloudWatch')
    }
```

5. **Rastreamento Distribuído com AWS X-Ray:**

```python
# Exemplo de função Lambda com rastreamento X-Ray
import json
import time
import aws_xray_sdk
from aws_xray_sdk.core import xray_recorder
from aws_xray_sdk.core import patch_all

patch_all()

def lambda_handler(event, context):
    with xray_recorder.in_segment('processamento'):
        time.sleep(5)  # Simula carga de trabalho
        return {
            'statusCode': 200,
            'body': json.dumps('Olá do Lambda com rastreamento X-Ray!')
        }
```

6. **Agregação de Logs:**

```python
import json
import logging

# Configura logging
logger = logging.getLogger()
logger.setLevel(logging.INFO)

def lambda_handler(event, context):
    logger.info('Processando evento: %s', json.dumps(event))
    return {
        'statusCode': 200,
        'body': json.dumps('Olá do Lambda com logging!')
    }
```

Esses trechos de código fornecem exemplos de implementação de vários aspectos de escalabilidade e monitoramento em aplicações serverless usando AWS Lambda e API Gateway.

### Perguntas de Entrevista Baseadas em Cenários

Perguntas de entrevista para um engenheiro DevOps com foco em arquitetura serverless, escalabilidade e monitoramento usando AWS Lambda e API Gateway:

1. **Você foi encarregado de otimizar o desempenho da nossa aplicação serverless implantada no AWS Lambda. Como garantiria que as funções Lambda pudessem lidar com picos repentinos de tráfego de forma eficaz?**

2. **Observamos uma degradação de desempenho durante as horas de pico de uso em nossa aplicação serverless. Como você ajustaria as configurações de concorrência das nossas funções Lambda para resolver esse problema?**

3. **Precisamos monitorar o desempenho das nossas funções Lambda em tempo real para garantir uma operação ideal. Como você implementaria soluções de monitoramento personalizadas usando métricas do CloudWatch?**

4. **Nossa equipe quer configurar alertas para erros de funções Lambda que excedam um determinado limite. Como você configuraria alarmes no CloudWatch para nos notificar quando ocorressem erros?**

5. **Esperamos um aumento significativo no tráfego para os endpoints do nosso API Gateway devido a uma campanha de marketing iminente. Como garantiria que o nosso API Gateway escalasse automaticamente para lidar com o aumento da carga?**

6. **Os endpoints do nosso API Gateway enfrentaram problemas de desempenho durante as horas de pico de uso. Como você analisaria o comportamento de escalabilidade do nosso API Gateway e identificaria possíveis gargalos?**

7. **Nossa equipe quer rastrear o número de solicitações atingindo os endpoints do nosso API Gateway ao longo do tempo. Como você implementaria soluções de monitoramento usando métricas do CloudWatch?**

8. **Precisamos identificar endpoints do API Gateway com altas taxas de erro para priorizar os esforços de resolução de problemas. Como você configuraria alarmes no CloudWatch para nos alertar quando as taxas de erro excederem os limites aceitáveis?**

9. **Nossa equipe quer obter insights sobre o desempenho da nossa aplicação serverless rastreando solicitações em funções Lambda e API Gateway. Como implementaria o rastreamento distribuído usando o AWS X-Ray?**

10. **Observamos gargalos de desempenho na nossa aplicação serverless, mas não temos certeza de onde eles se originam. Como usaria o AWS X-Ray para identificar a causa raiz desses problemas?**

### Conclusão

Neste post, exploramos os fundamentos da arquitetura serverless na AWS, incluindo Lambda, API Gateway, SNS e SQS. Ao aproveitar esses serviços, você pode construir aplicações escaláveis e orientadas por eventos com facilidade. Fique ligado para mais conteúdo empolgante sobre AWS em nossa jornada de 30 dias!

Isso conclui o Dia 22 do nosso curso AWS. Nos vemos amanhã!