---
title: "Dia 11: Lambda"
date: "2024-08-08"
tags: ["AWS", "Lambda", "Serverless"]
categories: ["Cloud"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia11"]
author: ["Edilson Freitas"]
cover:
  image: images/lambda.jpeg
  hiddenInList: true
---

## Bem-vindo de volta à nossa jornada de 30 dias no coração da Amazon Web Services (AWS).

Hoje, vamos mergulhar de cabeça no mundo da computação serverless com o AWS Lambda. Este serviço revolucionário permite que você execute código sem provisionar ou gerenciar servidores, tornando-se um divisor de águas para desenvolvedores e empresas.

## Compreendendo o AWS Lambda

A computação serverless emergiu como uma mudança de paradigma no mundo da computação em nuvem, e o AWS Lambda está na vanguarda dessa revolução. Vamos nos aprofundar no que a computação serverless implica e como o AWS Lambda se encaixa nessa visão.

### O que é Computação Serverless?

A computação serverless, apesar do nome, não significa que não há servidores envolvidos. Em vez disso, refere-se a um modelo de computação em nuvem onde os provedores de nuvem abstraem as tarefas de gerenciamento da infraestrutura, permitindo que os desenvolvedores se concentrem apenas em escrever e implantar código. Em essência, a computação serverless permite que os desenvolvedores construam e executem aplicações sem se preocupar com o provisionamento, escalabilidade e gerenciamento de servidores.

### Conceitos Chave do AWS Lambda

O AWS Lambda é a plataforma de computação serverless da Amazon, oferecendo uma gama de recursos e benefícios:

- **Execução Orientada por Eventos:** Funções Lambda são acionadas por eventos de várias fontes, como solicitações HTTP, uploads de arquivos para o Amazon S3, alterações em tabelas do DynamoDB, mensagens do Amazon SNS e mais. Esta arquitetura orientada por eventos permite aplicações altamente responsivas e escaláveis.
- **Preço por Uso:** Com o Lambda, você paga apenas pelo tempo de computação consumido pelas suas funções, medido em milissegundos. Não há custos iniciais ou taxas de manutenção contínuas, tornando-o uma opção econômica tanto para projetos de pequena escala quanto para aplicações de grande escala.
- **Auto Escalabilidade:** O Lambda escala automaticamente para lidar com solicitações de entrada, garantindo que suas funções possam lidar com qualquer carga de trabalho sem intervenção manual. Você não precisa se preocupar com o provisionamento ou gerenciamento de servidores; a AWS cuida da infraestrutura para você.
- **Suporte para Múltiplas Linguagens:** O Lambda suporta várias linguagens de programação, incluindo Node.js, Python, Java, .NET, Go e Ruby. Esta flexibilidade permite que os desenvolvedores escolham a linguagem com a qual estão mais confortáveis para escrever suas funções.

### Benefícios da Computação Serverless com Lambda

- **Redução de Sobrecarga Operacional:** Com a computação serverless, você não precisa mais gerenciar o provisionamento de servidores, atualizações do sistema operacional ou tarefas de manutenção de servidores. Isso libera tempo e recursos valiosos que podem ser redirecionados para construir e melhorar suas aplicações.
- **Aumento da Escalabilidade e Resiliência:** O Lambda escala automaticamente para lidar com solicitações de entrada, garantindo que sua aplicação possa lidar com picos súbitos de tráfego sem tempo de inatividade ou degradação de desempenho. Além disso, as funções Lambda são distribuídas por várias zonas de disponibilidade, aumentando a resiliência e a tolerância a falhas.
- **Tempo de Mercado mais Rápido:** A computação serverless permite que os desenvolvedores se concentrem em escrever código e construir funcionalidades, em vez de se preocupar com preocupações de infraestrutura. Isso resulta em ciclos de desenvolvimento mais rápidos e menor tempo de lançamento no mercado para novas aplicações e atualizações.
- **Economia de Custos:** Com o preço por uso, você paga apenas pelo tempo de computação consumido pelas suas funções, tornando o Lambda uma opção econômica tanto para projetos de pequena escala quanto para aplicações de grande escala. Além disso, você pode otimizar os custos aproveitando recursos como concorrência provisionada e preços baseados em recursos.

## Criando Funções Lambda

Isso é um recurso chave do AWS Lambda, proporcionando aos desenvolvedores a flexibilidade de escolher a linguagem que melhor se adapta às suas necessidades e expertise. Vamos explorar como você pode criar funções Lambda em diferentes linguagens de programação suportadas pelo AWS Lambda:

### 1. Node.js

O Node.js é um runtime popular para construir aplicações do lado do servidor usando JavaScript. Para criar uma função Lambda em Node.js:

- **Crie uma Nova Função Lambda:** Navegue até o console do AWS Lambda e clique em “Create function”.
- **Escolha o Runtime:** Selecione “Node.js” como o runtime para sua função.
- **Escreva Sua Função:** Escreva o código da sua função Lambda diretamente no editor do console do AWS Lambda ou carregue um arquivo .zip contendo seu código Node.js.
- **Configure as Configurações:** Configure a função handler e outras configurações conforme necessário.
- **Salve e Implante:** Salve sua função Lambda e implante-a no AWS Lambda.

```javascript
exports.handler = async (event) => {
    const response = {
        statusCode: 200,
        body: JSON.stringify('Olá da função Lambda em Node.js!'),
    };
    return response;
};
```

### 2. Python

O Python é amplamente usado para desenvolvimento serverless devido à sua simplicidade e legibilidade. Para criar uma função Lambda em Python:

- **Crie uma Nova Função Lambda:** Vá até o console do AWS Lambda e clique em “Create function”.
- **Escolha o Runtime:** Selecione “Python” como o runtime para sua função.
- **Escreva Sua Função:** Escreva o código da sua função Lambda diretamente no editor do console do AWS Lambda ou carregue um arquivo .zip contendo seu código Python.
- **Configure as Configurações:** Configure a função handler e outras configurações conforme necessário.
- **Salve e Implante:** Salve sua função Lambda e implante-a no AWS Lambda.

```python
def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': 'Olá da função Lambda em Python!'
    }
```

### 3. Java

O Java proporciona robustez e desempenho para a construção de aplicações de nível empresarial. Para criar uma função Lambda em Java:

- **Crie uma Nova Função Lambda:** Navegue até o console do AWS Lambda e clique em “Create function”.
- **Escolha o Runtime:** Selecione “Java” como o runtime para sua função.
- **Escreva Sua Função:** Escreva o código da sua função Lambda usando Java e empacote-o como um arquivo .jar.
- **Carregue Seu Arquivo .jar:** Carregue seu arquivo .jar contendo o código da função Lambda no AWS Lambda.
- **Configure as Configurações:** Configure a classe e método handler, alocação de memória e outras configurações conforme necessário.

```java
public class LambdaHandler implements RequestHandler<Object, String> {
    public String handleRequest(Object input, Context context) {
        return "Olá da função Lambda em Java!";
    }
}
```

## Integrando Lambda com Outros Serviços AWS

Isso é um de seus recursos mais poderosos, permitindo que os desenvolvedores construam aplicações altamente escaláveis e responsivas. O Lambda pode ser perfeitamente integrado com vários serviços AWS, permitindo arquiteturas orientadas por eventos e automatizando fluxos de trabalho. Vamos explorar algumas integrações comuns:

### 1. Amazon S3

O AWS Lambda pode ser acionado por eventos em buckets do Amazon S3, como criação, exclusão ou modificação de objetos. Essa integração é útil para automatizar tarefas como processamento de imagens, validação de arquivos ou transformação de dados.

**Exemplo de Caso de Uso:**

- Gerar automaticamente miniaturas para imagens carregadas em um bucket S3.
- Processar arquivos de log carregados no S3 e extrair insights valiosos ou realizar análises.

### 2. Amazon DynamoDB

Funções Lambda podem ser acionadas por alterações em tabelas do Amazon DynamoDB usando DynamoDB Streams. Essa integração permite que você reaja a modificações de dados em tempo real e acione lógica de negócios ou fluxos de trabalho personalizados.

**Exemplo de Caso de Uso:**

- Atualizar índices de pesquisa ou agregar dados em resposta a alterações em tabelas DynamoDB.
- Enviar notificações ou acionar alertas com base em mudanças específicas de dados.

### 3. Amazon SNS

O AWS Lambda pode se inscrever em tópicos do Amazon SNS e ser invocado sempre que uma mensagem é publicada no tópico. Essa integração permite que você construa arquiteturas orientadas por eventos e processe mensagens de várias fontes.

**Exemplo de Caso de Uso:**

- Processar notificações recebidas e acionar respostas automáticas com base em critérios específicos.
- Realizar validação de dados ou enriquecimento antes de publicar mensagens para sistemas a jusante.

### 4. Amazon API Gateway

Funções Lambda podem servir como serviços de backend para o Amazon API Gateway, permitindo que você construa APIs escaláveis e flexíveis sem gerenciar servidores. O API Gateway pode acionar funções Lambda em resposta a solicitações HTTP recebidas, permitindo arquiteturas de aplicações serverless.

**Exemplo de Caso de Uso:**

- Construir APIs RESTful para aplicações web e móveis, com funções Lambda lidando com processamento de solicitações e lógica de negócios.
- Implementar políticas de autenticação, autorização e limitação de taxa usando o API Gateway antes de

invocar funções Lambda.

### 5. Amazon CloudWatch Events

Funções Lambda podem ser agendadas para serem executadas em intervalos especificados usando Amazon CloudWatch Events. Essa integração permite que você automatize tarefas recorrentes, realize atividades de manutenção e orquestre fluxos de trabalho.

**Exemplo de Caso de Uso:**

- Backups agendados de dados armazenados em buckets do Amazon S3 ou tabelas do Amazon DynamoDB.
- Rotação de logs, limpeza ou arquivamento de arquivos de log armazenados no Amazon CloudWatch Logs.

## Exemplos de Código

Abaixo estão exemplos de snippets de código demonstrando como integrar o AWS Lambda com vários serviços AWS mencionados anteriormente:

### 1. Evento de Trigger do Amazon S3

```python
import boto3

s3_client = boto3.client('s3')

def lambda_handler(event, context):
    # Recuperar o nome do bucket e a chave do objeto do evento
    bucket_name = event['Records'][0]['s3']['bucket']['name']
    object_key = event['Records'][0]['s3']['object']['key']
    
    # Lógica de processamento aqui (ex.: gerar miniatura, processar arquivo, etc.)
    # Para demonstração, simplesmente registramos o nome do bucket e a chave do objeto
    print(f"Objeto '{object_key}' carregado no bucket '{bucket_name}'")

    return {
        'statusCode': 200,
        'body': 'Evento S3 processado com sucesso!'
    }
```

### 2. Evento de Trigger do DynamoDB Stream

```python
import boto3

dynamodb_client = boto3.client('dynamodb')

def lambda_handler(event, context):
    # Processar registros do stream do DynamoDB
    for record in event['Records']:
        # Extrair e processar registro do DynamoDB
        print('Registro DynamoDB:', record)
    
    return {
        'statusCode': 200,
        'body': 'Evento de stream do DynamoDB processado com sucesso!'
    }
```

### 3. Assinatura do Amazon SNS

```python
import boto3

sns_client = boto3.client('sns')

def lambda_handler(event, context):
    # Processar mensagem do SNS
    sns_message = event['Records'][0]['Sns']['Message']
    print('Mensagem SNS recebida:', sns_message)
    
    return {
        'statusCode': 200,
        'body': 'Mensagem SNS processada com sucesso!'
    }
```

### 4. Integração com o Amazon API Gateway

```python
def lambda_handler(event, context):
    # Processar solicitação HTTP recebida do API Gateway
    http_method = event['httpMethod']
    request_body = event['body']
    print(f'Solicitação {http_method} recebida com corpo: {request_body}')
    
    # Lógica de negócios aqui
    
    # Retornar resposta para o API Gateway
    return {
        'statusCode': 200,
        'body': 'Solicitação processada com sucesso!'
    }
```

### 5. Agendamento com Amazon CloudWatch Events

```python
def lambda_handler(event, context):
    # Executar tarefa agendada (ex.: backup, limpeza, etc.)
    print('Tarefa agendada executada!')
    
    return {
        'statusCode': 200,
        'body': 'Tarefa agendada executada com sucesso!'
    }
```

Esses snippets de código demonstram a estrutura básica das funções Lambda e como elas podem ser integradas com diferentes serviços AWS. Dependendo do seu caso de uso específico, você pode customizar essas funções para realizar as operações desejadas e lidar com os dados de evento adequadamente.

## Perguntas de Entrevista Baseadas em Cenários

Aqui estão perguntas de entrevista baseadas em cenários e respostas cobrindo os tópicos mencionados anteriormente:

**Cenário: Você pode explicar um cenário onde você utilizou o AWS Lambda em um projeto?**
- **Resposta:** Em um projeto anterior, tínhamos uma aplicação que exigia a geração de miniaturas para imagens carregadas em um bucket S3. Aproveitamos o AWS Lambda para acionar automaticamente a geração de miniaturas sempre que uma nova imagem era carregada no bucket S3 designado. A função Lambda escutava eventos S3 e processava cada nova imagem, gerando miniaturas de vários tamanhos para acomodar diferentes requisitos de exibição.

**Cenário: Como você lida com dependências em funções AWS Lambda?**
- **Resposta:** No AWS Lambda, você pode incluir dependências empacotando-as junto com seu código de função. Para Node.js, você inclui o diretório `node_modules` no seu pacote de implantação. Para outras linguagens, você precisa empacotar dependências manualmente ou usar ferramentas de gerenciamento de dependências como Maven para Java ou pip para Python.

**Cenário: Descreva uma situação onde você integrou o AWS Lambda com o Amazon DynamoDB.**
- **Resposta:** Em um projeto de análise em tempo real, integramos o AWS Lambda com DynamoDB Streams para capturar alterações em nossas tabelas DynamoDB. Sempre que um novo registro era inserido ou atualizado na tabela DynamoDB, a função Lambda era acionada pelo stream do DynamoDB. Usamos essa integração para realizar análises em tempo real e visualização das mudanças de dados.

**Cenário: Como você garante o processamento confiável de mensagens ao integrar o Lambda com o Amazon SNS?**
- **Resposta:** Ao integrar o Lambda com o Amazon SNS, é essencial implementar tratamento de erros e tentativas de repetição dentro da função Lambda. Além disso, configurar filas de dead-letter (DLQs) para funções Lambda garante que mensagens que não puderam ser processadas com sucesso sejam capturadas e possam ser analisadas posteriormente para fins de solução de problemas.

**Cenário: Você pode explicar como implementou o backup automático de dados armazenados em um bucket S3?**
- **Resposta:** Implementamos backups automáticos aproveitando o AWS Lambda e o Amazon CloudWatch Events. Agendamos uma função Lambda para ser executada periodicamente usando CloudWatch Events. A função Lambda copiava o conteúdo do bucket S3 especificado para outro destino, como outro bucket S3 ou Amazon Glacier, garantindo redundância de dados e recuperação de desastres.

**Cenário: Como você lida com uploads de arquivos grandes para um bucket S3?**
- **Resposta:** Para lidar com uploads de arquivos grandes para um bucket S3, podemos utilizar uploads multipartes. Isso nos permite fazer upload de grandes objetos em partes, que podem ser processadas e gerenciadas de forma mais eficiente. Os SDKs da AWS fornecem APIs para gerenciar uploads multipartes, permitindo que controlemos o processo de upload e lidemos com erros de forma graciosa.

**Cenário: Descreva um cenário onde você usou o Amazon API Gateway em conjunto com o AWS Lambda.**
- **Resposta:** Em uma arquitetura de microsserviços, usamos o Amazon API Gateway para expor APIs RESTful que serviam como ponto de entrada para nossa aplicação. Cada endpoint da API era suportado por uma função Lambda, que realizava a lógica de negócios necessária. Essa configuração nos permitiu construir uma arquitetura escalável e serverless, com o API Gateway lidando com autenticação, autorização e roteamento de solicitações.

**Cenário: Como você gerencia versionamento e implantação de APIs no Amazon API Gateway?**
- **Resposta:** No Amazon API Gateway, podemos gerenciar versões de API e implantações usando estágios. Cada estágio representa uma captura da configuração da API e endpoints em um ponto específico no tempo. Ao criar múltiplos estágios (ex.: desenvolvimento, teste, produção), podemos implantar e gerenciar mudanças em nossas APIs de forma segura sem impactar clientes existentes.

## Conclusão

O AWS Lambda revoluciona a maneira como pensamos em construir e implantar aplicações na nuvem. Ao abstrair a infraestrutura subjacente, o Lambda permite que os desenvolvedores se concentrem em escrever código que resolva problemas de negócios.

Isso conclui o Dia 11 de nossa jornada de 30 dias na AWS. Fique atento para a próxima sessão!
