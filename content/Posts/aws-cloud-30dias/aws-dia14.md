---
title: "Dia 14: CloudFront"
date: "2024-08-09T08:30:00-03:00"
description: "Explorando o Amazon CloudFront, uma poderosa ferramenta de entrega de conteúdo."
categories: ["Cloud"]
tags: ["Cloudfront", "CDN", "S3", "EC2"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia14"]
author: ["Edilson Freitas"]
cover:
  image: images/cloudfront.png
  hiddenInList: true
---

## Bem-vindo de volta à nossa jornada para dominar a AWS! 

Hoje, vamos mergulhar em uma das ferramentas mais poderosas para entrega de conteúdo — o Amazon CloudFront. À medida que avançamos, aprenderemos sobre sua importância, configuração e possibilidades de integração com outros serviços AWS, como S3 e EC2.

*Confira as perguntas de entrevista baseadas em cenários no final deste blog. Entre em contato se precisar de respostas para as perguntas!*

## Introdução ao CloudFront:

Vamos nos aprofundar na introdução ao CloudFront como uma rede de entrega de conteúdo (CDN).

### O que é uma Rede de Entrega de Conteúdo (CDN)?

Uma Rede de Entrega de Conteúdo (CDN) é uma rede geograficamente distribuída de servidores que trabalham juntos para fornecer entrega rápida de conteúdo da internet. As CDNs são projetadas para servir conteúdo da web, como páginas HTML, arquivos JavaScript, folhas de estilo, imagens e vídeos, aos usuários com base em sua localização geográfica, a origem do conteúdo e outros fatores. O objetivo principal de uma CDN é minimizar a latência e melhorar o desempenho geral das aplicações web, armazenando em cache o conteúdo mais próximo dos usuários finais.

### Entendendo o CloudFront como uma CDN

O Amazon CloudFront é um serviço de CDN globalmente distribuído oferecido pela Amazon Web Services (AWS). Ele fornece uma infraestrutura segura, escalável e de alto desempenho para entregar conteúdo web aos usuários em todo o mundo. O CloudFront utiliza uma rede de locais de borda estrategicamente localizados em várias regiões geográficas ao redor do mundo.

### Componentes Principais do CloudFront

- **Locais de Borda:** Estes são data centers localizados em várias partes do mundo onde cópias em cache do seu conteúdo são armazenadas. Os locais de borda atendem às solicitações de entrada para o seu conteúdo e armazenam em cache o conteúdo acessado com frequência para entrega mais rápida aos usuários.
- **Servidores de Origem:** Estes são os servidores originais onde seu conteúdo é armazenado, como buckets Amazon S3, instâncias Amazon EC2, Elastic Load Balancers ou origens personalizadas. O CloudFront recupera o conteúdo dos servidores de origem e o armazena em cache nos locais de borda para solicitações subsequentes.
- **Distribuições:** Uma distribuição é uma configuração do CloudFront que especifica os servidores de origem dos quais o CloudFront deve recuperar o conteúdo e as regras para entregar esse conteúdo aos usuários finais. Você pode criar várias distribuições para servir diferentes tipos de conteúdo ou para aplicar diferentes configurações de cache e segurança.

### Vantagens do CloudFront

- **Melhor Desempenho:** Ao armazenar em cache o conteúdo nos locais de borda mais próximos dos usuários finais, o CloudFront reduz a latência e melhora o desempenho geral das aplicações web.
- **Escalabilidade:** O CloudFront escala automaticamente para lidar com grandes volumes de tráfego, garantindo desempenho consistente mesmo durante picos de tráfego.
- **Alcance Global:** Com uma grande rede de locais de borda abrangendo vários continentes, o CloudFront permite que você alcance usuários em todo o mundo com latência mínima.
- **Segurança:** O CloudFront oferece recursos de segurança integrados, como suporte a HTTPS, integração com AWS Identity and Access Management (IAM) e proteção contra DDoS, garantindo a integridade e confidencialidade do seu conteúdo.
- **Custo-benefício:** O CloudFront oferece preços de pagamento conforme o uso, sem taxas iniciais ou compromissos de longo prazo. Você paga apenas pela transferência de dados e pelas solicitações atendidas pelo CDN.

## Configurando Distribuições e Comportamentos de Cache:

Configurar distribuições e comportamentos de cache é essencial para otimizar o desempenho da entrega de conteúdo e controlar como o CloudFront armazena em cache e serve seu conteúdo. Vamos nos aprofundar neste tópico em mais detalhes:

### Configurando Distribuições:

1. **Criando uma Distribuição:**

    - Para começar a configurar uma distribuição, faça login no seu AWS Management Console e navegue até o serviço CloudFront.
    - Clique em "Create Distribution" para iniciar o processo de configuração.
    - Escolha o método de entrega apropriado: Web ou RTMP (para streaming de mídia).
    - Especifique o(s) servidor(es) de origem dos quais o CloudFront buscará conteúdo. Isso pode ser um bucket Amazon S3, uma instância EC2, um Elastic Load Balancer ou uma origem personalizada.
    - Configure configurações adicionais, como comportamentos de cache, certificado SSL, registros e configurações de distribuição.

2. **Configurações de Cache:**

    - O CloudFront permite que você controle por quanto tempo diferentes tipos de conteúdo são armazenados em cache nos locais de borda usando as configurações de Time To Live (TTL).
    - Você pode definir comportamentos de cache padrão para todas as solicitações ou criar comportamentos de cache personalizados com base em padrões de caminho, cabeçalhos HTTP, strings de consulta, etc.
    - Configurar as configurações de cache envolve definir comportamentos para lidar com solicitações de tipos específicos de conteúdo, como arquivos estáticos, conteúdo dinâmico ou solicitações de API.

### Comportamentos de Cache:

1. **Comportamento de Cache Padrão:**

    - O comportamento de cache padrão se aplica a todas as solicitações que não correspondem a nenhum comportamento de cache personalizado.
    - Você pode especificar o TTL (Time To Live) padrão para diferentes métodos HTTP (GET, POST, etc.) e configurar se o CloudFront deve encaminhar determinados cabeçalhos para o servidor de origem ou não.
    - Além disso, você pode especificar se deseja comprimir objetos automaticamente antes de servi-los aos clientes.

2. **Comportamentos de Cache Personalizados:**

    - Comportamentos de cache personalizados permitem definir regras específicas de cache com base em padrões de caminho, strings de consulta ou cabeçalhos de solicitação.
    - Por exemplo, você pode querer armazenar em cache imagens e arquivos CSS por um período mais longo (por exemplo, uma semana), mas definir um TTL mais curto para conteúdo HTML dinâmico (por exemplo, alguns minutos).
    - Comportamentos de cache personalizados oferecem controle granular sobre como o CloudFront armazena em cache e serve diferentes tipos de conteúdo.

### Exemplo de Configuração:

**Comportamento de Cache Padrão:**
- Encaminhar Cabeçalhos: Nenhum
- Encaminhar Cookies: Nenhum
- Encaminhamento e Cache de String de Consulta: Encaminhar todos, armazenar em cache com base em todos
- Armazenamento em Cache de Objetos: Usar Cabeçalhos de Cache de Origem

**Comportamento de Cache Personalizado para Conteúdo Estático:**
- Padrão de Caminho: /static/*
- Encaminhar Cabeçalhos: Nenhum
- Encaminhamento e Cache de String de Consulta: Encaminhar todos, armazenar em cache com base em todos
- Armazenamento em Cache de Objetos: Personalizar (TTL: 604800 segundos)

**Comportamento de Cache Personalizado para Conteúdo Dinâmico:**
- Padrão de Caminho: /api/*
- Encaminhar Cabeçalhos: Todos
- Encaminhamento e Cache de String de Consulta: Encaminhar todos, armazenar em cache com base em todos
- Armazenamento em Cache de Objetos: Personalizar (TTL: 300 segundos)

## Integrando CloudFront com S3 e EC2:

Integrar o CloudFront com S3 e EC2 permite que você aproveite os benefícios de escalabilidade e desempenho do CloudFront para entregar conteúdo estático e dinâmico. Aqui está uma explicação detalhada de como você pode integrar o CloudFront com S3 e EC2:

### Integrando CloudFront com S3:

1. **Servindo Conteúdo Estático a partir do S3:**

    - O Amazon S3 é uma excelente escolha para armazenar conteúdo estático, como imagens, arquivos CSS, JavaScript e arquivos HTML.
    - Para integrar o CloudFront com o S3, você precisa criar uma distribuição do CloudFront e especificar seu bucket S3 como o servidor de origem.
    - Quando um usuário solicita um arquivo, o CloudFront primeiro verifica seu cache de borda. Se o arquivo não for encontrado, o CloudFront busca o arquivo do bucket S3, armazena em cache no local de borda e o serve ao usuário.
    - Esta configuração reduz a latência e melhora o desempenho ao servir conteúdo a partir do local de borda mais próximo do usuário.

2. **Etapas para Integrar CloudFront com S3:**

    - Crie uma nova distribuição do CloudFront a partir do AWS Management Console ou usando o AWS CLI.
    - Especifique seu bucket S3 como o nome de domínio de origem para a distribuição.
    - Configure outras configurações, como comportamentos de cache, certificado SSL e registros, conforme necessário.
    - Uma vez que a distribuição é criada, o CloudFront começará a armazenar em cache o conteúdo do seu bucket S3 nos locais de borda, melhorando a velocidade de entrega e reduzindo a carga no

 seu bucket S3.

### Integrando CloudFront com EC2:

1. **Acelerando a Entrega de Conteúdo Dinâmico:**

    - Embora o Amazon S3 seja ideal para conteúdo estático, o conteúdo dinâmico gerado por aplicações web executadas em instâncias Amazon EC2 também pode se beneficiar da aceleração do CloudFront.
    - Para integrar o CloudFront com EC2, você configura suas instâncias EC2 como servidores de origem para as distribuições do CloudFront.
    - Quando um usuário solicita conteúdo dinâmico, o CloudFront encaminha a solicitação para a instância EC2 de origem, armazena a resposta em cache nos locais de borda e serve solicitações subsequentes para o mesmo conteúdo a partir do cache.
    - Esta configuração descarrega o tráfego de suas instâncias EC2, reduz a latência para os usuários e melhora a escalabilidade e a confiabilidade da sua aplicação web.

2. **Etapas para Integrar CloudFront com EC2:**

    - Configure sua aplicação web executada no EC2 para servir conteúdo via HTTP ou HTTPS.
    - Crie uma distribuição do CloudFront e especifique sua instância EC2 como o servidor de origem, usando seu nome DNS público ou endereço IP.
    - Configure comportamentos de cache e outras configurações com base nos requisitos da sua aplicação.
    - Uma vez que a distribuição é implantada, o CloudFront armazenará em cache o conteúdo dinâmico nos locais de borda, acelerando a entrega aos usuários e reduzindo a carga nas suas instâncias EC2.

### Exemplos de Código

#### Exemplo 1: Criando uma Distribuição do CloudFront via AWS CLI

```bash
# Criando Distribuição do CloudFront
aws cloudfront create-distribution \
    --origin-domain-name meu-bucket.s3.amazonaws.com \
    --default-cache-behavior \
        "TargetOriginId=meu-bucket,ViewerProtocolPolicy=allow-all" \
    --viewer-certificate \
        "CloudFrontDefaultCertificate=true" \
    --distribution-config \
        "DefaultRootObject=index.html,Enabled=true"
```

#### Exemplo 2: Integrando CloudFront com S3 usando Boto3 (Python SDK)

```python
import boto3

# Criar um cliente do CloudFront
client = boto3.client('cloudfront')

# Criar uma distribuição do CloudFront
response = client.create_distribution(
    DistributionConfig={
        'CallerReference': 'minha-distribuicao',
        'Comment': 'Minha Distribuição do CloudFront',
        'DefaultCacheBehavior': {
            'TargetOriginId': 'meu-bucket',
            'ViewerProtocolPolicy': 'allow-all'
        },
        'Origins': {
            'Quantity': 1,
            'Items': [
                {
                    'DomainName': 'meu-bucket.s3.amazonaws.com',
                    'Id': 'meu-bucket',
                    'S3OriginConfig': {
                        'OriginAccessIdentity': ''
                    }
                }
            ]
        }
    }
)
```

#### Exemplo 3: Integrando CloudFront com EC2 usando Boto3 (Python SDK)

```python
import boto3

# Criar um cliente do CloudFront
client = boto3.client('cloudfront')

# Criar uma distribuição do CloudFront
response = client.create_distribution(
    DistributionConfig={
        'CallerReference': 'minha-distribuicao',
        'Comment': 'Minha Distribuição do CloudFront',
        'DefaultCacheBehavior': {
            'TargetOriginId': 'minha-instancia-ec2',
            'ViewerProtocolPolicy': 'allow-all'
        },
        'Origins': {
            'Quantity': 1,
            'Items': [
                {
                    'DomainName': 'minha-instancia-ec2.compute.amazonaws.com',
                    'Id': 'minha-instancia-ec2',
                    'CustomOriginConfig': {
                        'HTTPPort': 80,
                        'HTTPSPort': 443,
                        'OriginProtocolPolicy': 'http-only'
                    }
                }
            ]
        }
    }
)
```

### Notas:

- Substitua "meu-bucket" pelo nome do seu bucket S3 e "minha-instancia-ec2" pelo nome de domínio ou endereço IP da sua instância EC2.
- Certifique-se de que suas credenciais AWS estão configuradas corretamente para executar esses comandos.
- Ajuste outras configurações, como comportamentos de cache, certificados SSL e registros, conforme necessário.

Esses exemplos fornecem um ponto de partida para configurar distribuições do CloudFront e integrá-las com S3 e EC2. Você pode personalizar essas configurações com base no seu caso de uso específico e requisitos da aplicação.

### Perguntas de Entrevista Baseadas em Cenários

1. Sua empresa está planejando lançar uma nova aplicação web globalmente. Como você configuraria o CloudFront para otimizar o desempenho de uma aplicação web global?
2. Sua empresa está enfrentando aumento de latência na entrega de conteúdo de vídeo para usuários em diferentes regiões. Descreva como você configuraria o Amazon CloudFront para otimizar a entrega de conteúdo de vídeo para usuários em diferentes regiões.
3. Sua equipe precisa hospedar um site estático. Como você integraria o Amazon S3 com o CloudFront para hospedar um site estático?
4. Sua equipe precisa garantir alta disponibilidade e durabilidade para dados armazenados no Amazon S3. Como você configuraria o Amazon S3 para garantir alta disponibilidade e durabilidade para os dados armazenados?
5. Sua equipe está implantando uma aplicação web dinâmica em instâncias Amazon EC2. Como você integraria o Amazon EC2 com o CloudFront para acelerar a entrega de uma aplicação web dinâmica?
6. Sua equipe está implantando uma aplicação baseada em microsserviços em instâncias Amazon EC2. Explique como você usaria o Amazon CloudFront para implementar balanceamento de carga para uma aplicação baseada em microsserviços implantada em instâncias Amazon EC2.

## Conclusão

Em resumo, o CloudFront é um serviço de CDN poderoso que permite entregar conteúdo web para usuários em todo o mundo com baixa latência e alto desempenho. Ajustando as configurações de cache e criando comportamentos de cache personalizados, você pode garantir que seu conteúdo seja entregue de forma rápida e eficiente para usuários em todo o mundo, minimizando a carga nos seus servidores de origem.

Isso conclui nossa exploração do CloudFront para hoje. Amanhã, mergulharemos mais fundo em outro aspecto fascinante da AWS. Até lá, continue inovando na nuvem!
