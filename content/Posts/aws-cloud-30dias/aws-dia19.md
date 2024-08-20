---
title: "Dia 19: Otimização de Custos"
date: "2024-08-24"
description: "Em qualquer infraestrutura em nuvem, o gerenciamento de custos é fundamental, e a AWS oferece várias ferramentas e estratégias para ajudá-lo."
categories: ["Cloud"]
tags: ["AWSCost", "Budget", "AWS", "DevOps"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia19"]
author: ["Edilson Freitas"]
cover:
  image: images/cost.png
  hiddenInList: true
---

## Bem-vindo de volta ao Dia 19 do nosso Curso de Maestria em AWS de 30 Dias! 

Hoje, estamos mergulhando profundamente no tópico crucial de otimização de custos. Em qualquer infraestrutura em nuvem, o gerenciamento de custos é fundamental, e a AWS oferece várias ferramentas e estratégias para ajudá-lo a manter suas despesas sob controle enquanto maximiza a eficiência dos seus recursos.

Confira as perguntas baseadas em cenários no final deste blog, que podem ser úteis para entrevistas!

### Monitorando e Otimizando os Custos da AWS:

A monitoração e a otimização dos custos na AWS são aspectos críticos para gerenciar sua infraestrutura em nuvem de forma eficiente. A AWS oferece várias ferramentas e serviços para ajudá-lo a acompanhar, analisar e otimizar seus gastos. Vamos explorar esses aspectos em mais detalhes:

#### Monitorando Custos na AWS:

- **AWS Cost Explorer:** Essa ferramenta oferece uma visão abrangente dos seus gastos na AWS ao longo do tempo. Ela permite que você visualize seus custos usando gráficos e tabelas, facilitando a identificação de tendências e anomalias. Você pode detalhar serviços específicos, tipos de uso, regiões e tags para entender onde seu dinheiro está sendo gasto.
- **Painel de Gerenciamento de Faturamento e Custos:** O Painel de Gerenciamento de Faturamento e Custos fornece uma visão geral dos seus gastos acumulados no mês atual e faz previsões da sua fatura mensal estimada. Ele também destaca quaisquer anomalias de custos ou alertas de orçamento, ajudando você a manter suas despesas sob controle.
- **Relatórios de Uso e Custos:** A AWS oferece relatórios detalhados de uso e custos que fornecem insights granulares sobre seus gastos. Você pode personalizar esses relatórios para incluir pontos de dados específicos e baixá-los para análise adicional ou integração com ferramentas de terceiros.
- **Orçamentos e Alertas:** Os Orçamentos da AWS permitem que você defina orçamentos personalizados para seus gastos na AWS e receba alertas quando exceder ou estiver previsto para exceder os valores orçados. Essa abordagem proativa ajuda a evitar estouros inesperados de custos.

#### Otimizando Custos na AWS:

- **Dimensionamento Correto (Rightsizing):** Analise o uso dos seus recursos e ajuste os tamanhos ou tipos de instâncias para corresponder com precisão às necessidades da sua carga de trabalho. O dimensionamento correto ajuda a evitar o provisionamento excessivo, onde você paga por recursos desnecessários, e o provisionamento insuficiente, que pode causar problemas de desempenho.
- **Instâncias Reservadas (RIs) e Planos de Economia (Savings Plans):** RIs e Savings Plans oferecem descontos significativos em comparação com o preço sob demanda para instâncias EC2, bancos de dados RDS e outros serviços. Ao comprometer-se com um termo específico, você pode garantir taxas mais baixas e economizar dinheiro a longo prazo.
- **Instâncias Spot:** Instâncias Spot permitem que você faça lances em capacidade EC2 não utilizada a taxas significativamente reduzidas. Embora possam não ser adequadas para todas as cargas de trabalho devido à sua disponibilidade variável, elas podem proporcionar economias substanciais para aplicações tolerantes a falhas e flexíveis.
- **Auto Scaling:** Implemente Auto Scaling para ajustar automaticamente o número de instâncias EC2 em resposta à demanda. Ao dimensionar sua infraestrutura com base em flutuações de carga de trabalho, você pode evitar o provisionamento excessivo durante os horários de pico e reduzir custos durante os períodos de baixa demanda.
- **Otimização de Armazenamento:** Utilize políticas de ciclo de vida para o Amazon S3 para mover automaticamente objetos para classes de armazenamento de menor custo ou expirarem com base em regras predefinidas. Isso ajuda a otimizar os custos de armazenamento sem sacrificar a acessibilidade ou durabilidade.
- **Tagging de Recursos:** Implemente uma estratégia robusta de tagging para seus recursos da AWS. As tags permitem que você categorize e rastreie custos de maneira mais eficaz, facilitando a alocação de despesas e a identificação de oportunidades de otimização.

### Entendendo Modelos de Preço da AWS e o Cost Explorer:

Vamos discutir em detalhes sobre os modelos de preço da AWS e o Cost Explorer abaixo.
#### Modelos de Preço da AWS:

- **Sob Demanda (On-Demand):** Com o preço sob demanda, você paga pela capacidade computacional por hora ou por segundo, sem compromissos de longo prazo. Esse modelo oferece flexibilidade, mas pode ser mais caro em comparação com outras opções de preços, especialmente para cargas de trabalho de estado constante.
- **Instâncias Reservadas (RIs):** As RIs oferecem descontos significativos (até 75%) em comparação com o preço sob demanda, em troca de um compromisso com um tipo de instância específico, região e prazo (1 ou 3 anos). As RIs são ideais para cargas de trabalho previsíveis com padrões de uso estáveis.
- **Planos de Economia (Savings Plans):** Os Savings Plans oferecem descontos semelhantes às RIs, mas proporcionam mais flexibilidade ao permitir que você se comprometa com um valor específico por hora em vez de tipos de instância. Isso torna os Savings Plans adequados para uma gama mais ampla de serviços, incluindo EC2, Fargate, Lambda e mais.
- **Instâncias Spot:** Instâncias Spot permitem que você faça lances em capacidade EC2 não utilizada, geralmente a preços significativamente mais baixos do que instâncias sob demanda. Embora as Instâncias Spot possam proporcionar economias substanciais, elas estão sujeitas à disponibilidade e podem ser encerradas com aviso prévio.
- **Hosts Dedicados:** Hosts Dedicados permitem que você execute instâncias em servidores físicos dedicados ao seu uso. Esse modelo é ideal para requisitos de conformidade ou restrições de licenciamento de software, mas pode ser mais caro do que outras opções.
- **Pague conforme o Uso (Pay-As-You-Go):** Alguns serviços da AWS, como Amazon S3 e Amazon DynamoDB, oferecem preços "pay-as-you-go" com base no seu uso real. Você paga apenas pelo que usa, tornando essa uma opção econômica para cargas de trabalho variáveis.

#### AWS Cost Explorer:

O AWS Cost Explorer é uma ferramenta poderosa que ajuda você a visualizar, entender e gerenciar seus gastos na AWS. Veja como ele pode ajudar:

- **Visualização de Custos:** O Cost Explorer oferece gráficos e tabelas interativos que permitem visualizar seus gastos na AWS ao longo do tempo. Você pode visualizar custos por serviço, tipo de uso, tipo de instância, região e muito mais, permitindo que você identifique tendências e padrões em seus gastos.
- **Previsão:** O Cost Explorer pode prever sua fatura mensal estimada com base em seus padrões de uso atuais. Isso ajuda a planejar e orçar despesas futuras de maneira mais eficaz.
- **Análise de Custos:** Você pode detalhar categorias de custos específicas para entender o que está impulsionando seus gastos. Por exemplo, você pode analisar custos por tipo de instância EC2 ou classe de armazenamento Amazon S3 para identificar oportunidades de otimização.
- **Recomendações:** O Cost Explorer fornece recomendações para oportunidades de economia de custos, como a compra de RIs ou a implementação de Auto Scaling. Essas recomendações são baseadas nas melhores práticas da AWS e podem ajudá-lo a otimizar seus custos de forma mais eficiente.
- **Personalização:** O Cost Explorer permite que você personalize seus relatórios de custos e painéis para focar nas métricas mais importantes para sua organização. Você pode salvar e compartilhar essas personalizações com outros membros da equipe, facilitando a colaboração e a tomada de decisões.

### Implementando Estratégias de Economia de Custos e Tagging de Recursos:

Vamos explorar essas estratégias em detalhes:
#### Estratégias de Economia de Custos:

- **Dimensionamento Correto (Rightsizing):** Analise o uso dos seus recursos e ajuste tamanhos ou tipos de instâncias para corresponder com precisão às necessidades da sua carga de trabalho. Ao eliminar recursos superdimensionados, você pode reduzir custos sem sacrificar o desempenho.
- **Instâncias Reservadas (RIs) e Planos de Economia (Savings Plans):** Comprometa-se com um tipo de instância específico, região e prazo (1 ou 3 anos) para se beneficiar de descontos significativos em comparação com o preço sob demanda. Os Savings Plans oferecem descontos semelhantes, mas proporcionam mais flexibilidade ao permitir que você se comprometa com um valor específico por hora.
- **Instâncias Spot:** Faça lances em capacidade EC2 não utilizada a preços significativamente mais baixos do que instâncias sob demanda. As Instâncias Spot podem proporcionar economias substanciais para cargas de trabalho tolerantes a falhas e flexíveis, mas exigem arquitetura cuidadosa para lidar com interrupções.
- **Auto Scaling:** Ajuste automaticamente o número de instâncias EC2 com base na demanda. Ao dimensionar sua infraestrutura dinamicamente, você pode evitar o provisionamento excessivo durante os horários de pico e reduzir custos durante os períodos de baixa demanda.
- **Otimização de Armazenamento:** Utilize políticas de ciclo de vida para o Amazon S3 para mover automaticamente objetos para classes de armazenamento de menor custo ou expirarem com base em regras predefinidas. Isso ajuda a otimizar os custos de armazenamento sem sacrificar a acessibilidade ou durabilidade.
- **Otimização de Banco de Dados:** Considere usar a opção Aurora Serverless do Amazon Aurora ou aproveitar o modo de capacidade sob demanda do DynamoDB para dimensionar seus bancos de dados automaticamente com base na demanda de carga de trabalho. Isso pode ajudar você a economizar custos pagando apenas pelos recursos que você

consome.

#### Tagging de Recursos:

- **Categorização:** Implemente uma estratégia de tagging para categorizar seus recursos da AWS com base em atributos como ambiente (por exemplo, produção, desenvolvimento), aplicação, proprietário ou centro de custo. As tags fornecem metadados valiosos que podem ajudar você a entender e gerenciar seus custos de forma mais eficaz.
- **Alocação de Custos:** Use tags para alocar custos a projetos, equipes ou departamentos específicos dentro da sua organização. Isso permite um rastreamento de custos e faturamento mais preciso, facilitando a responsabilidade financeira e o gerenciamento de orçamentos.
- **Monitoramento de Custos:** Aproveite as tags no AWS Cost Explorer para filtrar e analisar seus gastos com base em critérios específicos. Por exemplo, você pode analisar custos por tag para identificar quais projetos ou equipes estão impulsionando as maiores despesas e implementar estratégias de otimização direcionadas.
- **Automação:** Incorpore tags nos seus fluxos de trabalho de automação para aplicar medidas de economia de custos automaticamente. Por exemplo, você pode configurar funções AWS Lambda para encerrar recursos sem tags ou ociosos após um determinado período, ajudando a prevenir custos desnecessários.
- **Governança:** Estabeleça políticas e diretrizes para tagging de recursos dentro da sua organização para garantir consistência e conformidade. Ao aplicar padrões de tagging, você pode manter visibilidade do seu ambiente AWS e facilitar os esforços de otimização de custos.

### Exemplos de Código para Implementar Estratégias de Economia de Custos e Tagging de Recursos na AWS:

**Exemplo 1: Implementando Auto Scaling**

```bash
# Criar um grupo de Auto Scaling
aws autoscaling create-auto-scaling-group \
    --auto-scaling-group-name meu-grupo-auto-scaling \
    --launch-configuration-name minha-configuracao-launch \
    --min-size 2 \
    --max-size 5 \
    --desired-capacity 3 \
    --availability-zones us-east-1a us-east-1b \
    --tags Key=Name,Value=meu-grupo-auto-scaling
```

**Exemplo 2: Implementando Políticas de Ciclo de Vida para o Amazon S3**

```bash
# Criar uma política de ciclo de vida para mover objetos para a classe de armazenamento Glacier após 30 dias
aws s3api put-bucket-lifecycle-configuration \
    --bucket meu-bucket \
    --lifecycle-configuration '{
        "Rules": [
            {
                "ID": "MoverParaGlacier",
                "Prefix": "",
                "Status": "Enabled",
                "Transitions": [
                    {
                        "Days": 30,
                        "StorageClass": "GLACIER"
                    }
                ]
            }
        ]
    }'
```

**Exemplo 3: Implementando Instâncias Reservadas (RIs)**

```bash
# Comprar uma Instância Reservada para um tipo de instância, prazo e região específicos
aws ec2 purchase-reserved-instances-offering \
    --instance-count 1 \
    --reserved-instances-offering-id abc123 \
    --instance-type m5.large \
    --availability-zone us-east-1a
```

**Exemplo 4: Implementando Tagging de Recursos**

```bash
# Taggear uma instância EC2 com as tags Nome e Ambiente
aws ec2 create-tags \
    --resources i-1234567890abcdef0 \
    --tags Key=Name,Value=MinhaInstancia Key=Environment,Value=Producao
```

**Exemplo 5: Analisando Custos por Tag usando AWS Cost Explorer (o AWS CLI não suporta diretamente a consulta de dados do Cost Explorer, mas você pode usar a API do AWS Cost Explorer)**

```python
# Código Python de exemplo para consultar a API do AWS Cost Explorer por custos por tag
import boto3

client = boto3.client('ce')

response = client.get_cost_and_usage(
    TimePeriod={
        'Start': '2024-03-01',
        'End': '2024-03-10'
    },
    Granularity='DAILY',
    Metrics=['BlendedCost'],
    GroupBy=[
        {
            'Type': 'DIMENSION',
            'Key': 'SERVICE'
        },
        {
            'Type': 'TAG',
            'Key': 'Environment'
        }
    ]
)

print(response)
```

Esses exemplos demonstram implementações práticas de estratégias de economia de custos, como Auto Scaling, políticas de ciclo de vida para o S3, compra de Instâncias Reservadas e tagging de recursos usando comandos do AWS CLI.

### Perguntas de Entrevista Baseadas em Cenários Focando em Otimização de Custos na AWS:

1. Descreva um cenário em que você teve que implementar Auto Scaling para otimizar custos em um ambiente AWS.
2. Você pode descrever uma situação em que implementou políticas de ciclo de vida para o Amazon S3 para otimizar custos de armazenamento?
3. Você já utilizou Instâncias Reservadas (RIs) para otimizar custos na AWS? Pode fornecer um exemplo?
4. Como você utilizou o tagging de recursos para gerenciar custos de forma eficaz na AWS?
5. Você pode descrever um cenário em que usou o AWS Cost Explorer para analisar custos por tag?

### Conclusão:

A otimização de custos na AWS é um processo contínuo que requer monitoramento, análise e ajustes constantes. Ao entender os modelos de preço da AWS, aproveitar ferramentas como o Cost Explorer e implementar estratégias de economia de custos, você pode gerenciar efetivamente suas despesas na AWS enquanto maximiza o valor da sua infraestrutura em nuvem.

Fique atento para o Dia 20, onde exploraremos Alta Disponibilidade e Recuperação de Desastres na AWS!