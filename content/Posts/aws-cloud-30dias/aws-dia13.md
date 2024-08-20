---
title: "Dia 13: CloudWatch"
date: "2024-08-09T08:10:00-03:00"
description: "Explorando as capacidades abrangentes de monitoramento e registro do AWS CloudWatch."
categories: ["Cloud"]
tags: ["CloudWatch", "AWS", "Monitoramento", "Registro", "Métricas", "Alarmes", "Logs"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia13"]
author: ["Edilson Freitas"]
cover:
  image: images/cloudwatch.png
  hiddenInList: true
---

## Bem-vindo ao Dia 13 da nossa jornada de 30 dias na AWS! 

Hoje, vamos explorar as capacidades abrangentes de monitoramento e registro do AWS CloudWatch. O CloudWatch é uma ferramenta essencial no ecossistema AWS, fornecendo insights sobre seus recursos e aplicações AWS. Cobriremos como criar métricas personalizadas, definir alarmes e analisar dados de log para garantir a saúde e o desempenho de seus serviços.

*Também confira as perguntas de entrevista baseadas em cenários no final deste blog. Entre em contato se precisar de respostas para as perguntas!*

## Visão Geral do Serviço de Monitoramento e Registro do CloudWatch

O AWS CloudWatch é um serviço versátil de monitoramento e observabilidade fornecido pela Amazon Web Services, que permite que desenvolvedores, operadores de sistemas e gerentes de TI obtenham insights em tempo real sobre seus recursos e aplicações AWS.

### Principais Funcionalidades do CloudWatch:

1. **Monitoramento de Desempenho:**
   O CloudWatch coleta e rastreia métricas, que são variáveis que você pode medir para seus recursos e aplicações. Essas métricas fornecem insights valiosos sobre a utilização da CPU, transferência de dados e latência de serviços AWS, como instâncias Amazon EC2, tabelas Amazon DynamoDB e instâncias Amazon RDS. Esses dados ajudam a entender o desempenho do sistema e garantir que os recursos estejam funcionando conforme o esperado.

2. **Métricas Personalizadas:**
   Além das métricas predefinidas fornecidas pelos serviços AWS, o CloudWatch permite publicar suas próprias métricas personalizadas. Isso pode ser particularmente útil para monitorar métricas específicas de aplicativos, como o número de transações ou taxas de erro, proporcionando flexibilidade para adaptar o monitoramento às necessidades específicas.

3. **Alarmes:**
   Alarmes do CloudWatch podem ser configurados para notificá-lo quando métricas específicas ultrapassarem limites definidos, indicando possíveis problemas. Esses alarmes podem acionar notificações ou iniciar automaticamente ações, como operações de escalonamento ou acionamento de funções AWS Lambda, ajudando a automatizar respostas a problemas potenciais.

4. **Gerenciamento de Logs:**
   O CloudWatch Logs permite coletar, monitorar e analisar arquivos de log de seus recursos AWS, aplicações e servidores locais. Este recurso permite entender e solucionar problemas operacionais, fornecendo um repositório centralizado para dados de log.

5. **Eventos e Automação:**
   CloudWatch Events (agora parte do Amazon EventBridge) permite responder a mudanças de estado em seus recursos AWS. Com o CloudWatch Events, você pode acionar fluxos de trabalho para funções AWS Lambda, tópicos Amazon SNS, filas Amazon SQS e mais, permitindo respostas operacionais automatizadas.

6. **Dashboard e Visualização:**
   O CloudWatch fornece dashboards personalizáveis que permitem criar representações visuais de suas métricas e logs. Esses dashboards podem ser configurados para exibir dados em tempo real, oferecendo uma visão consolidada dos recursos e aplicações que você está monitorando.

7. **Integração e Extensibilidade:**
   O CloudWatch se integra perfeitamente com outros serviços AWS, fornecendo uma solução de monitoramento unificada em todo o seu ambiente AWS. Ele também suporta várias APIs e SDKs, permitindo extensibilidade e integração com ferramentas e serviços de terceiros.

8. **Log Insights:**
   O CloudWatch Log Insights permite pesquisar e analisar interativamente seus dados de log no CloudWatch Logs. Você pode realizar consultas para ajudar a responder de forma mais eficiente e eficaz a problemas operacionais, se surgirem.

### Casos de Uso:

- **Monitoramento de Aplicações:** Obtenha insights sobre o desempenho das aplicações e a experiência do usuário, monitorando logs de aplicações e métricas personalizadas.
- **Otimização de Recursos:** Identifique recursos subutilizados para otimizar custos e desempenho, analisando padrões de uso.
- **Segurança e Conformidade:** Monitore e retenha arquivos de log para análise de segurança e auditoria de conformidade.
- **Solução de Problemas Operacionais:** Diagnostique e resolva rapidamente problemas operacionais, analisando logs e métricas.

## Criando Métricas Personalizadas e Alarmes:

É uma maneira poderosa de monitorar os aspectos específicos de suas aplicações e infraestrutura que são mais importantes para o seu negócio. Essa capacidade permite que você vá além das métricas padrão fornecidas pelos serviços AWS e adapte sua estratégia de monitoramento às suas necessidades exclusivas.

### Métricas Personalizadas
Métricas personalizadas no CloudWatch são métricas definidas pelo usuário que permitem monitorar pontos de dados específicos da aplicação ou métricas operacionais que o AWS não rastreia por padrão. Este recurso é particularmente útil para capturar e analisar dados que refletem o desempenho, uso ou estado de saúde da sua aplicação.

#### Como Criar Métricas Personalizadas:
1. **Coletar Dados:** Identifique os dados que você deseja monitorar. Isso pode ser qualquer coisa, desde o número de inscrições de usuários em sua aplicação, o tempo de resposta de um serviço interno crítico, até o tamanho da fila de um sistema de processamento.

2. **Publicar no CloudWatch:** Use a chamada de API 'PutMetricData' para enviar seus dados personalizados para o CloudWatch. Você pode fazer isso usando SDKs AWS em várias linguagens de programação, AWS CLI ou diretamente por meio de solicitações HTTP.

Aqui está um exemplo básico usando o SDK AWS para Python (Boto3):

```python
import boto3

# Inicializar o cliente CloudWatch
cloudwatch = boto3.client('cloudwatch')

# Publicar métrica personalizada
cloudwatch.put_metric_data(
    Namespace='SeuNamespacePersonalizado',
    MetricData=[
        {
            'MetricName': 'SeuNomeDeMetrica',
            'Dimensions': [
                {
                    'Name': 'NomeDaDimensao',
                    'Value': 'ValorDaDimensao'
                },
            ],
            'Value': 123,  # Seu valor de métrica
            'Unit': 'Count'  # Unidade da métrica, por exemplo, Seconds, Count, Bytes
        },
    ]
)
```

3. **Definir Dimensões (Opcional):** Dimensões são pares nome-valor que identificam exclusivamente uma métrica. Você pode incluir dimensões em sua métrica para categorizá-las e filtrá-las, por exemplo, por ID da instância, região ou versão da aplicação.

4. **Escolher Granularidade da Métrica:** A granularidade de uma métrica determina o quão detalhados seus dados são. O CloudWatch suporta granularidade de 1 minuto para métricas personalizadas, permitindo intervalos de monitoramento detalhados.

### Alarmes
Alarmes no CloudWatch são usados para acionar notificações ou ações automatizadas com base no valor de uma métrica que excede um limite predefinido. Eles são essenciais para monitoramento proativo e resposta automatizada a incidentes.

#### Como Criar Alarmes:
1. **Escolher uma Métrica:** Selecione a métrica para a qual deseja definir um alarme. Isso pode ser qualquer métrica existente dos serviços AWS ou sua própria métrica personalizada.

2. **Definir Limite:** Especifique o valor do limite que, quando ultrapassado, deve acionar o alarme. Isso envolve definir o operador de comparação (por exemplo, maior que, menor que) e o valor do limite.

3. **Definir Período de Avaliação:** Determine o período durante o qual a métrica é avaliada em relação ao seu limite. Isso define quanto tempo a métrica deve estar além do limite antes que o estado do alarme mude.

4. **Configurar Ações:** Decida o que acontece quando o estado do alarme muda. As ações podem incluir enviar notificações (por exemplo, via Amazon SNS), escalonar recursos automaticamente ou acionar funções AWS Lambda.

Aqui está um exemplo de criação de um alarme usando Boto3 para uma métrica personalizada:

```python
# Inicializar o cliente CloudWatch
cloudwatch = boto3.client('cloudwatch')

# Criar um alarme
cloudwatch.put_metric_alarm(
    AlarmName='SeuNomeDeAlarme',
    Namespace='SeuNamespacePersonalizado',
    MetricName='SeuNomeDeMetrica',
    Dimensions=[
        {
            'Name': 'NomeDaDimensao',
            'Value': 'ValorDaDimensao'
        },
    ],
    Statistic='Average',  # Pode ser Sum, Min, Max
    Period=300,  # Período em segundos
    EvaluationPeriods=1,  # Número de períodos para avaliar
    Threshold=100,  # Seu valor de limite
    ComparisonOperator='GreaterThanThreshold',  # Operador de comparação
    AlarmActions=['arn:aws:sns:region:id-conta:acao-alarme'],  # ARN do tópico SNS
    Unit='Count'
)
```

5. **Testar e Refinar:** Após configurar seus alarmes, é uma boa prática testá-los para garantir que se comportam conforme esperado. Isso pode envolver gerar as condições que acionam o alarme e verificar se as ações configuradas são executadas corretamente.

## Configurando Logs do CloudWatch e Analisando

Dados de Log:

Isso envolve uma série de etapas que permitem coletar, monitorar, armazenar e acessar informações de registro em todos os seus recursos e aplicações AWS. Este processo é crucial para entender o comportamento de seus sistemas, solucionar problemas e manter a saúde operacional.

### Configurando Logs do CloudWatch

1. **Criando Grupos de Logs e Streams de Logs:**

    - **Grupos de Logs:** Um grupo de logs é um contêiner que contém uma coleção de streams de logs. Você define grupos de logs, e cada grupo pode conter streams de logs de diferentes fontes. Os grupos de logs também definem por quanto tempo reter os dados de log.
    - **Streams de Logs:** Um stream de logs representa a sequência de eventos de log que compartilham a mesma fonte. Cada stream de logs dentro de um grupo de logs deve ter um nome único.

Para configurar um grupo de logs e um stream de logs:
1. Navegue até o console do CloudWatch em seu AWS Management Console.
2. Vá para a seção "Logs" e escolha "Create log group."
3. Especifique um nome para seu grupo de logs e escolha as configurações de retenção para seus logs.
4. Dentro do grupo de logs, crie um stream de logs escolhendo "Create log stream" e especificando um nome.

2. **Enviando Logs para o CloudWatch:**
   Logs podem ser enviados para o CloudWatch de diferentes fontes, como instâncias EC2, funções AWS Lambda ou servidores locais. Isso pode ser realizado usando o agente do CloudWatch Logs ou os SDKs AWS. Por exemplo, em uma instância EC2, você pode instalar e configurar o agente do CloudWatch Logs para monitorar arquivos de log específicos e enviar seus dados para o CloudWatch.

3. **Usando SDKs AWS ou CLI:**
   Você pode usar SDKs AWS ou a Interface de Linha de Comando (CLI) AWS para colocar dados de log em seus streams de log programaticamente. Este método permite mais flexibilidade e pode ser usado para integrar o registro de logs no fluxo de trabalho de sua aplicação.

### Analisando Dados de Log

1. **CloudWatch Logs Insights:**
   O CloudWatch Logs Insights fornece uma interface interativa para consultar e visualizar seus dados de log. Você pode realizar consultas para filtrar, classificar e agregar dados de log, tornando mais fácil entender e analisar.

Para usar o Logs Insights:
1. No console do CloudWatch, navegue até "Logs Insights."
2. Selecione o(s) grupo(s) de logs que deseja consultar.
3. Escreva sua consulta usando a sintaxe de consulta do Logs Insights. Você pode realizar buscas, filtrar dados e usar agregações para analisar seus logs.
4. Execute a consulta para visualizar os resultados. Você também pode visualizar os resultados em vários formatos, como gráficos de linha ou gráficos de barras.

2. **Monitoramento em Tempo Real com Filtros de Métrica:**
   Filtros de métrica permitem transformar dados de log em métricas numéricas do CloudWatch que você pode visualizar ou definir alarmes. Isso é útil para monitoramento em tempo real de dados de log para frases, valores ou padrões específicos.

Para criar um filtro de métrica:
1. No console do CloudWatch, vá para a seção "Logs" e selecione o grupo de logs que você está interessado.
2. Escolha "Metric filters" e depois "Create metric filter."
3. Defina o padrão de filtro que deseja corresponder e teste-o contra seus dados de log.
4. Especifique os detalhes da métrica, como nome, namespace e valor.
5. Você pode então usar essas métricas para criar alarmes ou adicioná-las a dashboards para monitoramento.

3. **Exportando Dados de Log:**
   Para análise ou arquivamento de longo prazo, você pode precisar exportar seus dados de log. O CloudWatch Logs permite exportar dados de log para buckets Amazon S3 para armazenamento ou análise adicional. Isso pode ser feito através do console do CloudWatch ou usando a CLI AWS.

### Perguntas de Entrevista Baseadas em Cenários

1. Você está monitorando uma aplicação executada em instâncias EC2 e percebe uma degradação intermitente de desempenho. Como você usaria o CloudWatch para identificar o problema?
2. Sua equipe implantou um novo serviço que processa arquivos de vídeo, e você foi encarregado de monitorar seu throughput. Descreva como você configuraria métricas personalizadas no CloudWatch para monitorar o número de arquivos de vídeo processados por minuto e criaria um alarme para quando o throughput cair abaixo de um determinado limite.
3. Você foi notificado sobre um pico de erros em uma aplicação web tarde da noite. Você suspeita que isso pode ser devido a uma implantação recente. Explique como usaria o CloudWatch Logs para confirmar se a implantação causou os erros e identificar quais são os erros.
4. Imagine que você é responsável pelo tempo de atividade de uma aplicação de produção crítica. Descreva como usaria o CloudWatch para monitorar proativamente e identificar problemas potenciais antes que afetem a disponibilidade da aplicação.
5. Sua organização quer monitorar KPIs de nível empresarial, como usuários ativos diários (DAUs) e receita por hora, dentro do AWS CloudWatch. Explique como você implementaria isso usando métricas personalizadas.
6. Você suspeita que pode haver tentativas de acesso não autorizado em suas instâncias EC2. Como usaria o CloudWatch Logs para investigar esse problema?
7. Você foi encarregado de melhorar o monitoramento de um conjunto de microsserviços implantados no ECS. Descreva como usaria o CloudWatch para aumentar a visibilidade do desempenho e da saúde do sistema.
8. Sua empresa tem um trabalho crítico noturno que deve ser concluído em até 3 horas. Descreva como usaria o CloudWatch para monitorar esse trabalho e alertar se estiver em risco de não ser concluído a tempo.
9. Após uma atualização recente, os usuários relatam problemas intermitentes com uma aplicação web. Descreva como usaria o CloudWatch Logs e Insights para isolar o problema.

## Conclusão:

O CloudWatch é uma ferramenta poderosa no conjunto de ferramentas AWS, fornecendo capacidades extensivas de monitoramento e registro. Ao aproveitar métricas personalizadas, alarmes e análise de logs, você pode manter a saúde e o desempenho de seus recursos e aplicações AWS.

Fique atento ao tópico de amanhã, onde exploraremos outro aspecto empolgante da AWS!
