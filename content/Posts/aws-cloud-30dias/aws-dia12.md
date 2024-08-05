---
title: "Dia 12: SNS (Simple Notification Service) e SQS (Simple Queue Service)"
date: "2024-08-09"
tags: ["AWS", "SNS", "SQS", "Messaging Services", "Pub/Sub", "Message Queues", "DevOps", "Cloud Computing", "Treinamento", "30 Days of AWS"]
categories: ["Cloud"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia12"]
author: ["Edilson Freitas"]
cover:
  image: images/snssqs.png
  hiddenInList: true
---

## Bem-vindo ao Dia 12 da nossa exploração de 30 dias na AWS!

Hoje, vamos mergulhar em dois poderosos serviços de mensagens fornecidos pela AWS: Simple Notification Service (SNS) e Simple Queue Service (SQS). Esses serviços são essenciais para construir aplicações escaláveis, flexíveis e desacopladas. Vamos detalhar suas funcionalidades, processos de configuração e implementar exemplos práticos para garantir que você tenha uma experiência prática.

## Compreendendo os serviços de mensagens SNS e SQS

Isso é crucial para aproveitar as capacidades poderosas de mensagens da AWS. Ambos os serviços facilitam a comunicação entre diferentes partes de suas aplicações de maneira confiável e escalável, mas servem a propósitos diferentes e operam sob modelos distintos.

### Amazon Simple Notification Service (SNS)

O Amazon SNS é um serviço gerenciado que fornece entrega de mensagens de publicadores para assinantes. Ele usa o paradigma de mensagens publish/subscribe (pub/sub).

- **Modelo Publish/Subscribe:** Neste modelo, publicadores enviam mensagens para um "tópico", que é um ponto de acesso lógico e canal de comunicação. Assinantes então recebem mensagens de tópicos aos quais estão inscritos. Uma única mensagem publicada em um tópico pode ser entregue a vários assinantes, permitindo um padrão de comunicação um-para-muitos.
- **Tópicos:** Os tópicos são o conceito central no SNS e atuam como um hub de distribuição de mensagens. Publicadores enviam mensagens para um tópico, e todos os assinantes desse tópico recebem a mensagem. Isso desacopla o produtor e o consumidor das mensagens.
- **Assinaturas:** Assinantes podem ser endpoints web, endereços de email, funções AWS Lambda, filas SQS e mais. Quando uma mensagem é publicada em um tópico, o SNS tenta entregar essa mensagem a cada assinante.
- **Casos de Uso:** O SNS é ideal para cenários como envio de notificações por email, acionamento de funções Lambda em resposta a eventos, ou encaminhamento de mensagens para filas SQS para processamento posterior.

### Amazon Simple Queue Service (SQS)

O Amazon SQS é um serviço de filas de mensagens totalmente gerenciado que permite desacoplar e escalar microsserviços, sistemas distribuídos e aplicações serverless.

- **Modelo de Filas de Mensagens:** O SQS usa um modelo pull-based onde mensagens são empurradas para uma fila por produtores e retiradas por consumidores ou trabalhadores. Isso permite o processamento assíncrono e desacopla os componentes de uma aplicação.
- **Filas:** No SQS, as filas são o componente principal, e elas armazenam mensagens que são transmitidas entre diferentes partes de sua aplicação. As mensagens são armazenadas na fila até serem processadas e excluídas por um consumidor.
- **Filas Padrão e FIFO:** O SQS oferece dois tipos de filas. Filas padrão fornecem máxima taxa de transferência, ordenação por melhor esforço e entrega pelo menos uma vez. Filas FIFO (First-In-First-Out) garantem que as mensagens sejam processadas exatamente uma vez, na ordem exata em que foram enviadas, o que é crucial para aplicações que exigem sequenciamento.
- **Timeout de Visibilidade:** Após uma mensagem ser recuperada por um consumidor, ela se torna invisível para outros consumidores por uma duração conhecida como "timeout de visibilidade". Isso impede que múltiplos consumidores processem a mesma mensagem simultaneamente.
- **Casos de Uso:** O SQS é adequado para tarefas como agendamento de trabalhos, processamento em lotes e desacoplamento de componentes de aplicação para garantir que a falha de um componente não impacte os outros.

### Integração do SNS e SQS

SNS e SQS podem ser integrados para combinar os benefícios de mensagens pub/sub e baseadas em filas. Por exemplo, um tópico SNS pode distribuir mensagens para várias filas SQS, permitindo arquiteturas complexas e escaláveis onde mensagens precisam ser processadas de múltiplas maneiras.

- **Padrão Fanout:** Este padrão de integração envolve um tópico SNS enviando mensagens para várias filas SQS. É útil para replicar dados em vários sistemas ou para processamento paralelo, onde cada fila SQS pode ser processada por diferentes consumidores.

## Configurando tópicos, assinaturas e notificações com SNS

Configurar esses componentes no SNS é um processo simples que permite distribuir mensagens de maneira eficiente para um grande número de assinantes através de vários protocolos. Aqui está um guia passo a passo para configurar esses componentes dentro do SNS:

### Passo 1: Criando um Tópico

Um tópico serve como um canal de comunicação no SNS. Veja como você pode criar um:

1. **Navegue até o SNS:** Faça login no Console de Gerenciamento da AWS, procure por SNS e abra o dashboard do SNS.
2. **Criar Tópico:** Clique em Topics na barra lateral esquerda e depois clique no botão Create topic.
3. **Escolha o Tipo de Tópico:** Você pode escolher entre um tópico padrão, que permite taxa de transferência ilimitada, ou um tópico FIFO (First-In-First-Out), que garante a ordem das mensagens e sem duplicatas.
4. **Configurar Detalhes do Tópico:** Forneça um nome para seu tópico e configure atributos adicionais conforme necessário. Nomes de tópicos devem ser únicos dentro de uma conta AWS.
5. **Criar:** Revise suas configurações e clique em Create topic para finalizar o processo de criação.

### Passo 2: Inscrevendo-se em um Tópico

As assinaturas definem como as mensagens publicadas em um tópico são entregues aos assinantes. Cada assinatura corresponde a um único endpoint (por exemplo, email, SMS, endpoint HTTP, função Lambda).

1. **Selecione Seu Tópico:** Na lista de tópicos, clique no tópico que você acabou de criar.
2. **Criar Assinatura:** Dentro da página de detalhes do tópico, encontre a seção Subscriptions e clique em Create subscription.
3. **Escolher Protocolo:** Selecione o protocolo com base em como você deseja receber notificações (por exemplo, Email, SMS, Lambda, SQS). Diferentes protocolos requerem diferentes tipos de endpoints (por exemplo, um endereço de email para o protocolo Email, um ARN de função Lambda para o protocolo Lambda).
4. **Especificar Endpoint:** Insira o endpoint que corresponde ao protocolo escolhido. Por exemplo, se você selecionou Email, você deve inserir um endereço de email onde deseja receber notificações.
5. **Criar:** Revise suas configurações e clique em Create subscription. Para certos protocolos como Email e SMS, o assinante deve confirmar a assinatura seguindo um link enviado para o endpoint antes que ela se torne ativa.

### Passo 3: Publicando Mensagens em um Tópico

Uma vez que você tenha um tópico e pelo menos uma assinatura, você pode começar a publicar mensagens:

1. **Navegue até Seu Tópico:** Vá para o dashboard do SNS, encontre seu tópico e clique nele para abrir a página de detalhes do tópico.
2. **Publicar Mensagem:** Clique no botão Publish message.
3. **Configurar Mensagem:** Insira a mensagem que deseja enviar. Você pode publicar uma mensagem de texto simples ou usar o formato JSON para mensagens estruturadas. Se necessário, você também pode definir atributos de mensagem para fins de filtragem.
4. **Enviar:** Clique em Publish message para enviar sua mensagem. Todos os assinantes do tópico receberão a mensagem de acordo com seu protocolo e endpoint de assinatura.

### Considerações Adicionais

- **Filtragem de Mensagens:** O SNS suporta filtragem de mensagens, o que permite que assinantes recebam apenas um subconjunto de mensagens com base nos atributos dessas mensagens. Isso pode ser configurado na política de filtro de assinatura.
- **Controle de Acesso:** Você pode controlar o acesso aos seus tópicos SNS usando políticas do AWS Identity and Access Management (IAM), garantindo que apenas usuários e serviços autorizados possam publicar ou se inscrever em seus tópicos.
- **Monitoramento e Log:** O SNS se integra com o Amazon CloudWatch e AWS CloudTrail, permitindo que você monitore o desempenho dos seus tópicos e registre todas as atividades de acesso e uso.

## Implementando filas de mensagens e trabalhadores com SQS

O SQS fornece uma fila de mensagens confiável, altamente escalável e hospedada para armazenar mensagens enquanto elas viajam entre computadores. Usando o SQS, você pode desacoplar os componentes de uma aplicação para que eles funcionem de maneira independente, facilitando o gerenciamento de mensagens entre componentes.

### Passo 1: Criando uma Fila SQS

1. **Acessar o SQS:** Faça login no Console de Gerenciamento da AWS, navegue até o dashboard do SQS.
2. **Criar Nova Fila:** Clique no botão Create queue. Você será solicitado a escolher entre uma fila Padrão e uma fila FIFO (First-In-First-Out).
    - **Fila Padrão:** Oferece máxima taxa de transferência, ordenação por melhor esforço e entrega pelo menos uma vez.
    - **Fila FIFO:** Proporciona os benefícios adicionais de entrega FIFO e processamento exatamente uma vez.
3. **Configurar Configurações da Fila:** Forneça um nome para sua fila e configure configurações como período de retenção

 de mensagens, tamanho máximo da mensagem, atraso de entrega e tempo de espera para receber mensagens, entre outros.
4. **Definir Permissões:** Configure permissões para sua fila para controlar quem pode enviar e receber mensagens.
5. **Criar Fila:** Revise suas configurações e crie a fila.

### Passo 2: Enviando Mensagens para a Fila

Trabalhadores ou aplicações podem enviar mensagens para a fila SQS, que serão armazenadas até que um consumidor as recupere.

1. **Selecionar Sua Fila:** No dashboard do SQS, encontre e selecione sua fila.
2. **Enviar Mensagem:** Clique no botão Send and receive messages.
3. **Compor Mensagem:** Insira o corpo da mensagem. Você também pode adicionar atributos de mensagem, se necessário, que são úteis para filtragem ou fornecimento de informações adicionais sobre a mensagem.
4. **Enviar:** Clique em Send message. A mensagem agora está colocada na fila e será armazenada até que seja processada e excluída por um consumidor.

### Passo 3: Processando Mensagens com Trabalhadores

Trabalhadores são aplicações ou serviços que continuamente fazem polling nas filas SQS para processar mensagens. Aqui está um esboço simples de como um trabalhador pode processar mensagens de uma fila SQS:

1. **Fazer Poll na Fila:** O trabalhador recupera mensagens da fila chamando a ação ReceiveMessage. Você pode especificar o número de mensagens para recuperar em uma única chamada (até 10).
2. **Processar a Mensagem:** Após receber a mensagem, o trabalhador pode processar a mensagem de acordo com a lógica de sua aplicação.
3. **Excluir a Mensagem:** Uma vez que a mensagem seja processada com sucesso, é crucial excluí-la da fila para evitar que seja processada novamente. Isso é feito chamando a ação DeleteMessage com o handle de recibo da mensagem, que é fornecido quando a mensagem é recuperada.

### Implementando Trabalhadores

Trabalhadores podem ser implementados de várias maneiras dependendo dos requisitos de sua aplicação e dos serviços AWS que você está usando. Por exemplo:

- **Instâncias EC2:** Você pode executar aplicações em instâncias EC2 que fazem polling na fila SQS, processam mensagens e depois as excluem.
- **AWS Lambda:** Você pode acionar uma função Lambda para processar mensagens na fila SQS. Essa abordagem serverless permite que você execute código sem provisionar ou gerenciar servidores.
- **Serviços de Contêiner:** Para aplicações containerizadas, serviços como Amazon ECS ou EKS podem ser usados para implantar contêineres que atuam como trabalhadores para processar mensagens SQS.

### Melhores Práticas

- **Timeout de Visibilidade:** Ajuste o timeout de visibilidade para garantir que as mensagens não sejam disponibilizadas prematuramente para outros trabalhadores antes do processamento atual ser concluído.
- **Tratamento de Erros:** Implemente tratamento de erros robusto em seus trabalhadores para lidar com falhas de processamento, incluindo tentativas de repetição e filas de mensagens mortas para mensagens que não podem ser processadas com sucesso.
- **Escalabilidade:** Monitore o desempenho da fila e dos trabalhadores para escalar seus recursos de acordo com a carga de trabalho. O AWS Auto Scaling pode ajudar a ajustar o número de instâncias ou funções Lambda com base na demanda.

## Exemplos de Código

Abaixo estão exemplos de snippets de código ilustrando como interagir com os serviços AWS SNS e SQS. Esses exemplos assumem que você tem o AWS SDK instalado e configurado corretamente com suas credenciais e região preferida.

### Exemplo SNS: Criando um Tópico, Inscrevendo-se no Tópico e Publicando uma Mensagem

```python
import boto3

# Inicializar o cliente SNS
sns_client = boto3.client('sns')

# Criar um tópico SNS
topic_response = sns_client.create_topic(Name='MyNotificationTopic')
topic_arn = topic_response['TopicArn']
print(f"Created Topic ARN: {topic_arn}")

# Inscrever um endereço de email no tópico
email_address = 'example@example.com'  # Substitua por um endereço de email válido
subscription_response = sns_client.subscribe(
    TopicArn=topic_arn,
    Protocol='email',
    Endpoint=email_address
)
print(f"Subscription ARN: {subscription_response['SubscriptionArn']}")

# Publicar uma mensagem no tópico
publish_response = sns_client.publish(
    TopicArn=topic_arn,
    Message='Hello, this is a test message from SNS!',
    Subject='Test SNS Message'
)
print(f"Message ID: {publish_response['MessageId']}")
```

### Exemplo SQS: Criando uma Fila, Enviando uma Mensagem e Recebendo/Excluindo uma Mensagem

```python
import boto3

# Inicializar o cliente SQS
sqs_client = boto3.client('sqs')

# Criar uma fila SQS
queue_response = sqs_client.create_queue(QueueName='MyQueue')
queue_url = queue_response['QueueUrl']
print(f"Created Queue URL: {queue_url}")

# Enviar uma mensagem para a fila
send_response = sqs_client.send_message(
    QueueUrl=queue_url,
    MessageBody='This is a test message for SQS'
)
print(f"Message ID: {send_response['MessageId']}")

# Receber uma mensagem da fila
receive_response = sqs_client.receive_message(
    QueueUrl=queue_url,
    MaxNumberOfMessages=1,  # Número de mensagens para recuperar
    WaitTimeSeconds=10  # Long polling
)

messages = receive_response.get('Messages', [])
if messages:
    message = messages[0]
    receipt_handle = message['ReceiptHandle']
    print(f"Received Message: {message['Body']}")

    # Excluir a mensagem da fila após o processamento
    delete_response = sqs_client.delete_message(
        QueueUrl=queue_url,
        ReceiptHandle=receipt_handle
    )
    print("Message deleted successfully")
else:
    print("No messages in queue")
```

### Nota:

- **Confirmação de Assinatura de Email do SNS:** Para a assinatura de email do SNS, o assinante (endereço de email fornecido) precisa confirmar a assinatura clicando em um link de confirmação que a AWS envia para o endereço de email antes que ele possa receber notificações.
- **Long Polling no SQS:** O parâmetro `WaitTimeSeconds` na chamada `receive_message` é configurado para habilitar o long polling. O long polling ajuda a reduzir o número de respostas vazias permitindo que o serviço SQS espere até que uma mensagem esteja disponível na fila antes de enviar uma resposta.
- **Tratamento de Erros:** É importante incluir tratamento de erros no código de produção para gerenciar exceções e erros que possam ocorrer durante as chamadas da API.
- **Limpeza:** Lembre-se de excluir o tópico SNS e a fila SQS que você criou durante os testes para evitar incorrer em cobranças desnecessárias na sua conta AWS.

Esses exemplos destinam-se a fornecer um ponto de partida para interagir com os serviços AWS SNS e SQS. Você pode expandir esses exemplos com base nos requisitos específicos de sua aplicação e nas melhores práticas da AWS.

## Perguntas de Entrevista Baseadas em Cenários

Aqui estão perguntas de entrevista baseadas em cenários e respostas relacionadas ao AWS SNS, SQS e práticas gerais de DevOps:

**Cenário:** Você precisa projetar um sistema onde uma aplicação publica relatórios financeiros, e vários departamentos (RH, Finanças, Operações) precisam acessar esses relatórios em tempo real. Como você projetaria isso usando serviços AWS?
- **Resposta:** Eu usaria o Amazon SNS para criar um tópico para publicar os relatórios financeiros. Cada departamento se inscreveria nesse tópico SNS usando o protocolo que melhor se adequa ao seu padrão de consumo (por exemplo, email, SQS para aplicações, Lambda para processamento e roteamento). Esse design garante a entrega em tempo real dos relatórios para todos os departamentos e desacopla o processo de geração de relatórios do consumo dos mesmos.

**Cenário:** Sua aplicação precisa processar pedidos de uma plataforma de e-commerce onde a sequência de processamento dos pedidos é crucial e deve ocorrer exatamente uma vez. Como você garantiria isso usando AWS?
- **Resposta:** Eu usaria filas FIFO (First-In-First-Out) do Amazon SQS para este cenário. Filas FIFO garantem que mensagens (pedidos, neste caso) sejam processadas na ordem exata em que foram enviadas e que cada mensagem seja processada exatamente uma vez, eliminando duplicatas. Isso é crucial para sistemas de processamento de pedidos onde a sequência e a unicidade de cada pedido são importantes.

**Cenário:** Você notou que algumas mensagens estão falhando ao processar corretamente em seu sistema de processamento de mensagens SQS. Como você lidaria com essas mensagens falhadas para depurar e manter a integridade do seu sistema de processamento de mensagens?
- **Resposta:** Eu implementaria uma fila de mensagens mortas (DLQ) no SQS para lidar com mensagens que falham ao processar corretamente após várias tentativas. A DLQ coletaria essas mensagens falhadas, permitindo que eu analisasse e depurasse o problema sem interromper o fluxo principal de processamento de mensagens. Além disso, eu configuraria alarmes do CloudWatch para me notificar quando mensagens estiverem sendo enviadas para a DLQ para resolução proativa de problemas.

**Cenário:** Descreva como você implementaria um pipeline CI/CD para uma arquitetura de microsserviços na AWS.
- **Resposta:** Para uma arquitetura de microsserviços, eu usaria o AWS CodePipeline para o processo CI/CD, com pipelines separados para cada

microsserviço para permitir implantação e escalabilidade independentes. O AWS CodeBuild executaria testes unitários e de integração, e contêineres Docker seriam usados para empacotar cada microsserviço. Esses contêineres seriam então implantados no Amazon ECS ou EKS para orquestração. Eu também integraria o AWS CodeDeploy para implantações blue/green para minimizar o tempo de inatividade e possibilitar rollback em caso de problemas.

**Cenário:** Como você garante implantações sem tempo de inatividade no seu ambiente AWS atual?
- **Resposta:** Para garantir implantações sem tempo de inatividade, eu uso técnicas de implantação blue/green. Por exemplo, em um ambiente EC2, eu manteria dois ambientes de produção (Blue e Green). Ao implantar uma nova versão, eu a implantaria no ambiente Green, que está ocioso no momento. Após a implantação e testes completos, eu redirecionaria o tráfego do Blue para o Green usando Route 53 ou um Elastic Load Balancer. Se surgirem problemas, eu poderia rapidamente reverter para o ambiente Blue. Para aplicações containerizadas, estratégias semelhantes podem ser implementadas usando ECS ou EKS com atualizações contínuas ou implantações canário.

**Cenário:** Sua equipe está enfrentando problemas com drift de configuração em seus ambientes em nuvem. Como você resolveria esse problema?
- **Resposta:** Para gerenciar o drift de configuração, eu usaria ferramentas de Infraestrutura como Código (IaC) como o AWS CloudFormation ou Terraform. Isso garante que todo o provisionamento de infraestrutura e configurações sejam definidos em código, versionados e possam ser aplicados de maneira consistente em todos os ambientes. Além disso, eu implementaria detecção de drift regular usando AWS Config ou os recursos de gerenciamento de estado do Terraform para identificar e corrigir discrepâncias. Automatizar os processos de implantação e atualização através de pipelines CI/CD reduz ainda mais a probabilidade de drift de configuração.

## Conclusão

Dominar o AWS Simple Notification Service (SNS) e o Simple Queue Service (SQS) é essencial para qualquer engenheiro DevOps que deseja projetar e gerenciar aplicações baseadas em nuvem escaláveis, resilientes e eficientes. Ao longo da nossa exploração, vimos como o SNS permite sistemas robustos de mensagens pub/sub, permitindo o desacoplamento dos componentes da aplicação e garantindo que as mensagens cheguem a múltiplos assinantes de maneira confiável. O SQS complementa isso fornecendo um sistema de filas de mensagens seguro e durável, garantindo que as mensagens sejam processadas na ordem e sem perda, mesmo sob alta taxa de transferência.

Isso conclui o Dia 12 da nossa jornada de 30 dias na AWS. Fique ligado para aprender mais sobre os serviços AWS!
