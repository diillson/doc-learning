---
title: "Dia 9: Route 53"
date: "2024-08-06"
description: "No dia 9 do nosso curso de 30 dias sobre AWS, exploramos o Route 53, o serviço DNS altamente escalável e confiável da Amazon. Aprenda sobre os principais recursos, configuração de registros DNS, implementação de verificações de integridade e otimização de tráfego com políticas de roteamento."
tags: ["AWS", "Route 53", "DNS", "Cloud", "DevOps", "30DiasAWS", "Treinamento"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia9"]
author: ["Edilson Freitas"]
cover:
  image: images/route53.jpg
  hiddenInList: true
---

## Bem-vindo ao Dia 9 do nosso curso de 30 dias sobre AWS!

Hoje, vamos nos aprofundar no Route 53, o serviço DNS (Domain Name System) altamente escalável e confiável da Amazon. O Route 53 oferece uma infinidade de recursos para gerenciar seus nomes de domínio e direcionar o tráfego da internet de maneira eficiente. Vamos explorar os principais conceitos e funcionalidades do Route 53.

Confira também as perguntas e respostas baseadas em cenários no final deste blog, que são úteis para entrevistas!

## Introdução ao serviço DNS do Route 53

O Route 53 é um serviço de DNS escalável e altamente disponível oferecido pela Amazon Web Services (AWS). Ele é nomeado após a porta TCP/IP 53, onde as solicitações de DNS são endereçadas. O Route 53 traduz efetivamente nomes de domínio legíveis por humanos (como exemplo.com) em endereços IP (como 192.0.2.1) que os computadores usam para identificar uns aos outros na internet.

### Principais Recursos do Route 53

- **Escalabilidade:** O Route 53 é projetado para lidar com grandes volumes de consultas DNS sem degradação de desempenho. Ele pode escalar automaticamente para gerenciar mudanças nos padrões de tráfego e cargas de consulta.
- **Alta Disponibilidade:** O Route 53 é construído na mesma infraestrutura que alimenta outros serviços da AWS. Ele é distribuído por vários data centers geograficamente diversos, garantindo alta disponibilidade e confiabilidade na resolução de DNS.
- **Cobertura Global:** O Route 53 possui uma rede global de servidores DNS estrategicamente localizados ao redor do mundo. Isso garante uma resolução rápida e confiável de DNS para usuários que acessam suas aplicações de diferentes regiões geográficas.
- **Integração com Serviços da AWS:** O Route 53 se integra perfeitamente com outros serviços da AWS, como Elastic Load Balancing (ELB), Amazon S3, Amazon EC2 e mais. Isso permite que você mapeie facilmente nomes de domínio para seus recursos da AWS e gerencie o roteamento de tráfego de forma eficiente.
- **Políticas de Roteamento Avançadas:** O Route 53 suporta várias políticas de roteamento, como roteamento simples, roteamento ponderado, roteamento baseado em latência, roteamento geográfico e roteamento de failover. Essas políticas permitem implementar estratégias sofisticadas de gerenciamento de tráfego com base em seus requisitos específicos.
- **Verificações de Integridade:** O Route 53 fornece verificações de integridade para monitorar a saúde e a disponibilidade de seus recursos. Você pode configurar verificações de integridade para endpoints como servidores web, balanceadores de carga e mais. O Route 53 roteia automaticamente o tráfego para longe de endpoints não saudáveis, ajudando a manter alta disponibilidade e confiabilidade.
- **Failover de DNS:** O Route 53 oferece funcionalidade de failover de DNS, que redireciona automaticamente o tráfego de um recurso falho ou não saudável para um recurso saudável. Isso ajuda a minimizar o tempo de inatividade e garante a disponibilidade contínua de suas aplicações.

### Casos de Uso do Route 53

- **Hospedagem de Sites:** O Route 53 pode ser usado para hospedar os registros DNS do seu site, incluindo o mapeamento de nomes de domínio para servidores web e a configuração de subdomínios.
- **Balanceamento de Carga:** O Route 53 funciona perfeitamente com Elastic Load Balancers (ELB) para distribuir o tráfego de entrada entre várias instâncias EC2 ou contêineres, garantindo desempenho ideal e tolerância a falhas.
- **Recuperação de Desastres:** O recurso de failover de DNS do Route 53 pode ser usado para implementar estratégias de recuperação de desastres redirecionando automaticamente o tráfego para recursos de backup em caso de falha do recurso primário.
- **Aplicações Globais:** A cobertura global e o roteamento baseado em latência do Route 53 permitem que você construa e implante aplicações que ofereçam experiências de baixa latência para usuários em todo o mundo.
- **Ambientes de Nuvem Híbrida:** O Route 53 pode ser integrado com infraestrutura local e ambientes de nuvem híbrida, permitindo que você gerencie DNS para recursos baseados em nuvem e tradicionais a partir de uma única interface.

## Configurando Registros DNS e Verificações de Integridade

Vamos explorar como configurar registros DNS e verificações de integridade no Route 53.

### Configuração de Registros DNS

Os registros DNS no Route 53 definem como os nomes de domínio são mapeados para recursos como instâncias EC2, buckets S3, balanceadores de carga e outros serviços da AWS. Aqui estão alguns tipos comuns de registros DNS e seus propósitos:

- **Registros A (Address Record):** Mapeia um nome de domínio para o endereço IPv4 do servidor que hospeda o domínio. Isso é comumente usado para apontar nomes de domínio para servidores web ou outra infraestrutura.
- **Registros AAAA (IPv6 Address Record):** Semelhante aos registros A, mas usados para mapear nomes de domínio para endereços IPv6.
- **Registros CNAME (Canonical Name Record):** Aponta um domínio ou subdomínio para o nome canônico de outro domínio. Isso é frequentemente usado para criar aliases para domínios.
- **Registros Alias:** Registros específicos do Route 53 que funcionam de maneira semelhante aos registros CNAME, mas com alguns benefícios adicionais, como suporte para mapeamento de apex de zona e atualização automática de endereços IP.
- **Registros MX (Mail Exchange Record):** Especifica servidores de troca de e-mail para o domínio, permitindo que você receba e-mails para seu domínio.

Aqui está como você pode configurar registros DNS no Route 53:

- **Usando o Console de Gerenciamento da AWS:** Navegue até o console do Route 53, selecione a zona hospedada para seu domínio e, em seguida, crie ou edite registros DNS usando a interface fornecida.
- **Usando a AWS CLI:** Você pode usar a AWS CLI para gerenciar registros DNS do Route 53 programaticamente. Comandos como `aws route53 change-resource-record-sets` permitem adicionar, atualizar ou excluir registros DNS em suas zonas hospedadas.
- **Usando SDKs da AWS:** SDKs da AWS para várias linguagens de programação fornecem APIs para interagir programaticamente com o Route 53, permitindo que você automatize tarefas de gerenciamento de DNS em suas aplicações.

### Configuração de Verificações de Integridade

As verificações de integridade no Route 53 permitem monitorar a saúde e a disponibilidade de seus recursos, como servidores web, balanceadores de carga e endpoints. O Route 53 envia periodicamente solicitações de verificação de integridade para seus recursos e avalia suas respostas para determinar seu status de saúde.

Aqui está como você pode configurar verificações de integridade no Route 53:

1. **Definir Configurações de Verificação de Integridade:** Especifique o endpoint ou recurso que você deseja monitorar, juntamente com o protocolo (HTTP, HTTPS, TCP ou HTTPS), porta e outras configurações relevantes.
2. **Configurar Limiares e Intervalos:** Configure a frequência e os limiares para verificações de integridade, incluindo o número de verificações consecutivas falhas necessárias para considerar um recurso não saudável e o intervalo entre as verificações.
3. **Configurar Verificadores de Integridade:** Escolha as regiões de onde os verificadores de integridade do Route 53 enviarão solicitações para seus recursos. Distribuir verificadores de integridade em várias regiões ajuda a garantir monitoramento preciso e capacidades de failover.
4. **Associar Verificações de Integridade com Registros DNS:** Associe verificações de integridade aos registros DNS que roteiam tráfego para seus recursos. O Route 53 roteia automaticamente o tráfego para longe de recursos não saudáveis com base nos resultados das verificações de integridade.

Configurando verificações de integridade no Route 53, você pode garantir a alta disponibilidade e a confiabilidade de suas aplicações redirecionando automaticamente o tráfego para longe de recursos não saudáveis e minimizando o tempo de inatividade.

## Implementando Políticas de Roteamento e Roteamento Baseado em Latência

Isso permite otimizar a distribuição de tráfego e melhorar o desempenho de suas aplicações. Vamos nos aprofundar nos detalhes:

### Políticas de Roteamento no Route 53

O Route 53 suporta várias políticas de roteamento, cada uma projetada para atender a requisitos específicos de gerenciamento de tráfego e cenários de failover:

1. **Política de Roteamento Simples:**
    - Esta é a política de roteamento mais básica, onde você associa um único registro DNS a um único recurso. Quando uma consulta DNS é recebida, o Route 53 responde com o endereço IP associado ao registro DNS.
    - Útil para direcionar tráfego para um único recurso, como um

 servidor web ou um balanceador de carga.

2. **Política de Roteamento Ponderado:**
    - Com o roteamento ponderado, você pode distribuir o tráfego entre vários recursos com base em pesos atribuídos.
    - Por exemplo, você pode alocar 70% do tráfego para um recurso e 30% para outro para realizar testes A/B ou transferir gradualmente o tráfego durante implantações.

3. **Política de Roteamento Baseado em Latência:**
    - O roteamento baseado em latência direciona o tráfego para o recurso com a menor latência de rede com base na localização geográfica do usuário.
    - O Route 53 mede a latência de várias localidades ao redor do mundo e direciona o tráfego para o recurso que fornece o melhor desempenho para cada usuário.
    - Ideal para aplicações globais onde minimizar a latência é crucial para a experiência do usuário.

4. **Política de Roteamento de Failover:**
    - O roteamento de failover é usado para criar configurações de failover ativo-passivo. Você designa um recurso como primário e outro como standby.
    - O Route 53 redireciona automaticamente o tráfego para o recurso de standby se o recurso primário se tornar indisponível.
    - Comumente usado para cenários de recuperação de desastres.

5. **Política de Roteamento Geográfico:**
    - O roteamento geográfico permite direcionar o tráfego com base na localização geográfica do usuário.
    - Você pode definir políticas de roteamento específicas para diferentes regiões ou países, garantindo que os usuários sejam direcionados aos recursos mais próximos ou mais apropriados.

### Roteamento Baseado em Latência

O roteamento baseado em latência é particularmente poderoso para otimizar o desempenho de aplicações distribuídas globalmente. Aqui está como funciona:

1. **Verificações de Integridade do Route 53:**
    - O Route 53 monitora continuamente a saúde e o desempenho de seus recursos usando verificações de integridade.
    - Isso garante que apenas recursos saudáveis e responsivos sejam considerados ao calcular a latência.

2. **Medições de Latência:**
    - O Route 53 mede a latência entre os usuários finais e seus recursos de várias regiões da AWS.
    - Ele usa essas informações para determinar o recurso ideal para o qual o tráfego deve ser direcionado com base na menor latência.

3. **Distribuição de Tráfego:**
    - Quando o Route 53 recebe uma consulta DNS, ele avalia a latência para cada recurso e direciona a consulta para o recurso com a menor latência para aquele usuário específico.
    - Isso garante que os usuários sejam automaticamente direcionados ao recurso que oferece o melhor desempenho de sua localização.

### Implementação

Para implementar o roteamento baseado em latência no Route 53:

1. **Criar Registros de Recursos:**
    - Defina os registros DNS para seus recursos (por exemplo, instâncias EC2, endpoints ELB) em sua zona hospedada no Route 53.

2. **Ativar o Roteamento Baseado em Latência:**
    - No console do Route 53, crie um novo conjunto de registros e selecione “Latência” como a política de roteamento.
    - Especifique as regiões onde seus recursos estão localizados e associe cada região aos registros DNS correspondentes.

3. **Verificações de Integridade e Monitoramento:**
    - Certifique-se de que as verificações de integridade estejam configuradas para seus recursos para manter alta disponibilidade e confiabilidade.
    - Monitore a latência e a saúde dos recursos através do console do Route 53 ou métricas do CloudWatch para identificar quaisquer problemas de desempenho.

Abaixo estão exemplos de snippets de código demonstrando como interagir com o AWS Route 53 usando a AWS CLI e o SDK Python (boto3). Cobriremos a criação de registros DNS, configuração de verificações de integridade e implementação de roteamento baseado em latência.

### Criando Registros DNS usando AWS CLI

```sh
# Crie um novo registro A no Route 53
aws route53 change-resource-record-sets \
    --hosted-zone-id SEU_ID_DA_ZONA_HOSPEDADA \
    --change-batch file://change_batch.json
```

O conteúdo de `change_batch.json`:

```json
{
  "Comment": "Criar um novo registro A",
  "Changes": [
    {
      "Action": "CREATE",
      "ResourceRecordSet": {
        "Name": "example.com",
        "Type": "A",
        "TTL": 300,
        "ResourceRecords": [
          {
            "Value": "192.0.2.1"
          }
        ]
      }
    }
  ]
}
```

### Configurando Verificações de Integridade usando AWS CLI

```sh
# Crie uma verificação de integridade para um endpoint
aws route53 create-health-check \
    --caller-reference minha-verificacao-de-integridade \
    --health-check-config \
        IPAddress=192.0.2.1,Port=80,Type=HTTP
```

### Implementando Roteamento Baseado em Latência usando Python (boto3)

```python
import boto3

# Crie um cliente do Route 53
route53_client = boto3.client('route53')

# Defina a política de roteamento baseada em latência
routing_policy = {
    'LoadBalancerName': 'meu-load-balancer',
    'Type': 'Latency'
}

# Crie um conjunto de registros de roteamento baseado em latência
response = route53_client.change_resource_record_sets(
    HostedZoneId='SEU_ID_DA_ZONA_HOSPEDADA',
    ChangeBatch={
        'Changes': [
            {
                'Action': 'CREATE',
                'ResourceRecordSet': {
                    'Name': 'example.com',
                    'Type': 'A',
                    'TTL': 300,
                    'ResourceRecords': [
                        {
                            'Value': 'ALIAS example.com.'
                        }
                    ],
                    'AliasTarget': {
                        'HostedZoneId': 'Z2FDTNDATAQYW2',  # ALIAS para o balanceador de carga
                        'DNSName': 'meu-load-balancer.us-west-2.elb.amazonaws.com',
                        'EvaluateTargetHealth': False
                    },
                    'SetIdentifier': 'us-west-2'  # Identificador para o roteamento baseado em latência
                }
            }
        ]
    }
)
```

Substitua os placeholders como `SEU_ID_DA_ZONA_HOSPEDADA` pelo ID da sua zona hospedada no Route 53. Para o código Python, você precisa ter o `boto3` instalado e configurado com suas credenciais da AWS. Certifique-se de que as permissões adequadas do IAM estão configuradas para executar esses comandos ou usar o script Python.

Esses exemplos fornecem um ponto de partida para interagir programaticamente com o Route 53. Você pode estender e personalizar esses scripts com base em seus requisitos específicos e casos de uso.

### Perguntas Baseadas em Cenários para Entrevistas

Abaixo estão perguntas de entrevistas baseadas em cenários e respostas para um papel de engenheiro DevOps focando no AWS Route 53:

**Cenário — Configuração e Gerenciamento de DNS: Explique a importância do gerenciamento de DNS em um ambiente DevOps.**
- **Resposta:** O gerenciamento de DNS é crucial em um ambiente DevOps, pois permite alocação eficiente de recursos e descoberta de serviços. Com o DNS, podemos mapear facilmente nomes de domínio legíveis por humanos para recursos específicos, como instâncias EC2, balanceadores de carga e buckets S3. Isso possibilita comunicação perfeita entre diferentes componentes de nossa infraestrutura e garante alta disponibilidade e tolerância a falhas.

**Cenário — Configuração e Gerenciamento de DNS: Descreva um cenário onde você usaria Registros Alias do Route 53 em vez de registros CNAME tradicionais.**
- **Resposta:** Os Registros Alias são usados quando precisamos mapear o domínio apex (por exemplo, example.com) diretamente para recursos da AWS, como ELB (Elastic Load Balancer) ou distribuições CloudFront. Ao contrário dos registros CNAME, os Registros Alias funcionam perfeitamente com recursos da AWS, fornecem melhor desempenho e suportam mapeamento de apex de zona sem custos adicionais.

**Cenário — Verificações de Integridade e Failover: Como você configuraria verificações de integridade no Route 53 para uma aplicação executando em múltiplas instâncias EC2 atrás de um balanceador de carga?**
- **Resposta:** Para configurar verificações de integridade, eu configuraria verificações de integridade do Route 53 para monitorar a saúde dos endpoints do balanceador de carga enviando solicitações periódicas para URLs específicas associadas a cada instância. Essas verificações de integridade verificariam a capacidade de resposta e a disponibilidade da aplicação. Em caso de falha, o Route 53 redirecionaria automaticamente o tráfego para longe das instâncias não saudáveis para garantir disponibilidade contínua e confiabilidade da aplicação.

**Cenário — Verificações de Integridade e Failover: Explique a importância de implementar políticas de roteamento de failover em uma arquitetura altamente disponível.**
- **Resposta:** Políticas de roteamento de failover são essenciais para garantir a continuidade do serviço em caso de falhas na infraestrutura. Configurando políticas de roteamento de failover no Route 53, podemos designar recursos primários e de standby para serviços críticos. Se o recurso primário se tornar indisponível por qualquer motivo, o Route 53

redireciona automaticamente o tráfego para o recurso de standby, minimizando o tempo de inatividade e mantendo a disponibilidade do serviço para os usuários finais.

**Cenário — Roteamento Baseado em Latência: Como você aproveitaria o roteamento baseado em latência do Route 53 para otimizar o desempenho de uma aplicação distribuída globalmente?**
- **Resposta:** O roteamento baseado em latência permite direcionar os usuários para os recursos mais próximos e responsivos com base em sua localização geográfica. Para otimizar o desempenho de uma aplicação distribuída globalmente, eu configuraria roteamento baseado em latência no Route 53 criando conjuntos de registros para cada região e associando-os aos recursos correspondentes. Isso garante que os usuários sejam automaticamente direcionados ao recurso com a menor latência, melhorando assim sua experiência geral.

**Cenário — Roteamento Baseado em Latência: Você pode descrever um cenário onde o roteamento baseado em latência pode não ser a escolha ideal para uma aplicação específica?**
- **Resposta:** Embora o roteamento baseado em latência seja eficaz para otimizar o desempenho na maioria dos cenários, ele pode não ser a escolha ideal para aplicações onde a localização dos usuários não impacta significativamente sua experiência ou quando a consistência entre regiões é mais crítica do que a otimização da latência. Nesses casos, uma política de roteamento mais simples, como roteamento ponderado ou roteamento geográfico, pode ser mais adequada.

## Conclusão

O Route 53 é uma ferramenta poderosa para gerenciar DNS e rotear tráfego de maneira eficaz dentro e fora da AWS. Compreender seus recursos e configurações é essencial para construir aplicações web escaláveis e confiáveis.

Fique atento ao tópico de amanhã enquanto continuamos nossa jornada pela AWS!