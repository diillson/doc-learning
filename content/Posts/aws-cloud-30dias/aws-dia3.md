---
title: "Dia 3: EC2 (Elastic Compute Cloud)"
date: 2024-07-31
tags: ["AWS", "Cloud Computing", "EC2", "Segurança", "Key Pairs", "Devops", "Treinamento"]
description: "Explore o EC2 da AWS, entenda os tipos de instâncias, como lançar sua primeira instância e gerenciar grupos de segurança e pares de chaves para acesso seguro."
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia3"]
author: ["Edilson Freitas"]
cover:
  image: images/ec2.jpg
  hiddenInList: true
---

## Bem-vindo de volta à nossa jornada de 30 dias para dominar a AWS!

🚀 Hoje, vamos mergulhar no coração da computação da AWS com o Elastic Compute Cloud (EC2). O EC2 é a pedra angular da computação em nuvem, oferecendo servidores virtuais escaláveis para uma ampla gama de aplicações.

### Introdução às instâncias EC2 e seus tipos

O Amazon Elastic Compute Cloud (EC2) é um serviço web fornecido pela Amazon Web Services (AWS) que permite aos usuários alugar computadores virtuais nos quais podem executar suas próprias aplicações. As instâncias EC2 fornecem capacidade de computação escalável na nuvem da AWS, permitindo que os usuários lancem e gerenciem máquinas virtuais (VMs) com várias configurações para atender às suas necessidades específicas de computação.

Aqui estão alguns pontos chave para entender sobre as instâncias EC2:

- **Escalabilidade:** As instâncias EC2 oferecem escalabilidade, permitindo que os usuários escalem facilmente seus recursos de computação para cima ou para baixo com base na demanda. Esta flexibilidade é particularmente útil para aplicações com cargas de trabalho flutuantes ou para lidar com picos súbitos de tráfego.
- **Variedade de Tipos de Instância:** A AWS fornece uma grande variedade de tipos de instância EC2, cada um otimizado para diferentes casos de uso e cargas de trabalho. Esses tipos de instância variam em termos de poder de computação, memória, armazenamento e capacidades de rede, permitindo que os usuários escolham o tipo de instância mais apropriado para suas aplicações.
- **Modelo de Preços Pay-As-You-Go:** Com o EC2, os usuários pagam apenas pela capacidade de computação que usam, seguindo um modelo de preços pay-as-you-go. Isso significa que os usuários podem facilmente escalar sua infraestrutura enquanto pagam apenas pelos recursos que consomem, sem custos iniciais ou compromissos de longo prazo.
- **Integração com VPC (Virtual Private Cloud):** As instâncias EC2 podem ser lançadas dentro de uma Virtual Private Cloud (VPC), o que permite aos usuários definir uma topologia de rede virtual e controlar o acesso à rede para suas instâncias. Isso fornece segurança e isolamento aprimorados para as instâncias EC2 executadas dentro da VPC.

### Tipos de Instâncias EC2

A AWS oferece uma ampla gama de tipos de instância EC2, cada um otimizado para casos de uso e cargas de trabalho específicos. Alguns dos tipos mais comuns de instâncias EC2 incluem:

- **Instâncias de Uso Geral:** Essas instâncias fornecem um equilíbrio de recursos de computação, memória e rede, tornando-as adequadas para uma ampla variedade de cargas de trabalho, incluindo servidores web, pequenos bancos de dados e ambientes de desenvolvimento. Exemplos incluem as instâncias t2.micro, t3.medium e m5.large.
- **Instâncias Otimizadas para Computação:** Essas instâncias são otimizadas para cargas de trabalho intensivas em computação que requerem processadores de alto desempenho. Elas são ideais para aplicações como computação de alto desempenho (HPC), modelagem científica e processamento em lote. Exemplos incluem as instâncias c5.large, c5.xlarge e c5.4xlarge.
- **Instâncias Otimizadas para Memória:** Essas instâncias são projetadas para cargas de trabalho intensivas em memória que requerem uma grande quantidade de RAM para processar e analisar dados. Elas são bem adequadas para bancos de dados em memória, análises em tempo real e aplicações de computação de alto desempenho (HPC). Exemplos incluem as instâncias r5.large, r5.xlarge e r5.4xlarge.
- **Instâncias Otimizadas para Armazenamento:** Essas instâncias são otimizadas para cargas de trabalho intensivas em armazenamento que requerem soluções de armazenamento de alto desempenho. Elas são ideais para aplicações como data warehousing, processamento de logs e entrega de conteúdo. Exemplos incluem as instâncias i3.large, i3.xlarge e i3.4xlarge.

Cada tipo de instância vem com diferentes combinações de CPU, memória, armazenamento e capacidades de rede, permitindo que os usuários escolham o tipo de instância que melhor se adapta aos seus requisitos específicos e restrições de orçamento.

### Lançando sua primeira instância EC2

Este é um passo fundamental para começar com o Amazon EC2. Abaixo está um guia detalhado sobre como lançar sua primeira instância EC2:

1. **Faça login no Console de Gerenciamento da AWS:**
   - Navegue até o [Console de Gerenciamento da AWS](https://aws.amazon.com/console/) e faça login com suas credenciais da conta AWS.

2. **Navegue até o Dashboard do EC2:**
   - Depois de fazer login no Console de Gerenciamento da AWS, você pode navegar até o dashboard do EC2 clicando no menu “Services” no topo da página e selecionando “EC2” na seção “Compute”. Isso o levará ao dashboard do EC2, onde você pode gerenciar suas instâncias EC2 e outros recursos.

3. **Lançar Instância:**
   - Uma vez no dashboard do EC2, localize a seção “Instances” no painel de navegação à esquerda e clique no link “Instances”. Em seguida, clique no botão “Launch Instance” para iniciar o assistente de criação de instâncias.

4. **Escolher uma Imagem de Máquina Amazon (AMI):**
   - No assistente de criação de instâncias, você será solicitado a escolher uma Imagem de Máquina Amazon (AMI) para sua instância. Uma AMI é um template pré-configurado que contém o sistema operacional e outros softwares necessários para lançar sua instância. Você pode escolher entre uma grande variedade de AMIs fornecidas pela AWS e pela comunidade. Por exemplo, você pode selecionar a “Amazon Linux 2 AMI” como ponto de partida para sua instância.

5. **Escolher um Tipo de Instância:**
   - Depois de selecionar uma AMI, você precisará escolher um tipo de instância para sua instância EC2. Tipos de instância definem as especificações de hardware virtual da sua instância, incluindo CPU, memória, armazenamento e desempenho de rede. A AWS oferece uma variedade de tipos de instância otimizados para diferentes casos de uso e cargas de trabalho. Para iniciantes, você pode começar com um tipo de instância de uso geral, como “t2.micro”, que é elegível para o Free Tier da AWS.

6. **Configurar Detalhes da Instância:**
   - Nesta etapa, você pode configurar detalhes adicionais para sua instância, incluindo o número de instâncias a serem lançadas, configurações de rede, funções IAM e scripts de dados do usuário. Você pode deixar a maioria das configurações em seus valores padrão por enquanto, mas pode querer personalizar as configurações com base em seus requisitos específicos.

7. **Adicionar Armazenamento:**
   - Em seguida, você pode adicionar volumes de armazenamento à sua instância. Por padrão, a AWS fornece um volume root para sua instância, mas você pode adicionar volumes adicionais se necessário. Você pode especificar o tipo de volume, tamanho e configurações de criptografia para cada volume.

8. **Configurar Grupo de Segurança:**
   - Nesta etapa, você configurará o grupo de segurança para sua instância. Um grupo de segurança atua como um firewall virtual que controla o tráfego de entrada e saída para sua instância. Você pode definir regras para permitir ou negar tráfego com base em protocolos, portas e endereços IP. Por exemplo, você pode querer permitir tráfego SSH (porta 22) e HTTP (porta 80) para sua instância.

9. **Revisar e Lançar:**
   - Depois de configurar todos os detalhes da instância, você pode revisar suas configurações e fazer as alterações necessárias. Uma vez satisfeito com a configuração, clique no botão “Launch” para iniciar o processo de criação da instância.

10. **Criar Par de Chaves:**
    - Antes de lançar sua instância, você será solicitado a criar ou selecionar um par de chaves existente para acesso SSH à sua instância. Um par de chaves consiste em uma chave pública e uma chave privada. A chave privada será usada para autenticar suas conexões SSH com a instância, enquanto a chave pública será armazenada na instância para fins de autenticação. Certifique-se de baixar o arquivo da chave privada e mantê-lo em um local seguro, pois você precisará dele para se conectar à sua instância via SSH.

11. **Acessar Sua Instância:**
    - Uma vez que sua instância esteja lançada, você pode acessá-la usando SSH ou outros protocolos de acesso remoto. Use o arquivo da chave privada que você baixou anteriormente para autenticar sua conexão SSH com a instância. O nome de usuário para a conexão SSH dependerá da AMI selecionada. Por exemplo, se você escolheu a Amazon Linux 2 AMI, o nome de usuário padrão será “ec2-user”.

### Entendendo grupos de segurança e pares de chaves

É crucial gerenciar a segurança de suas instâncias EC2 de forma eficaz. Vamos nos aprofundar em cada um

 desses conceitos:

#### 1. Grupos de Segurança:

Grupos de segurança atuam como firewalls virtuais para suas instâncias EC2, controlando o tráfego de entrada e saída. Eles permitem que você especifique regras que ditam quais tráfego é permitido alcançar suas instâncias e qual tráfego não é. Aqui estão alguns pontos chave sobre grupos de segurança:

- **Regras de Entrada:** Regras de entrada controlam o tráfego que é permitido alcançar suas instâncias EC2 da internet ou outras fontes de rede. Você pode definir regras de entrada com base em protocolos (por exemplo, TCP, UDP), portas (por exemplo, 22 para SSH, 80 para HTTP) e endereços IP ou blocos CIDR.
- **Regras de Saída:** Regras de saída controlam o tráfego que é permitido sair de suas instâncias EC2 e se comunicar com outros servidores ou serviços. Por padrão, todo o tráfego de saída é permitido, mas você pode restringi-lo definindo regras de saída específicas.
- **Filtragem com Estado:** Grupos de segurança usam filtragem com estado, o que significa que qualquer tráfego permitido para entrar é automaticamente permitido para sair, independentemente das regras de saída. Isso simplifica a configuração dos grupos de segurança e ajuda a garantir que o tráfego de resposta não seja bloqueado inadvertidamente.
- **Atualizações Dinâmicas:** As regras dos grupos de segurança podem ser atualizadas dinamicamente, permitindo que você modifique as regras para se adaptar a requisitos ou ameaças de segurança em mudança sem precisar reiniciar suas instâncias.
- **Associação de Grupos de Segurança:** Você pode associar um ou mais grupos de segurança com cada instância EC2. Isso permite que você aplique diferentes conjuntos de regras a diferentes instâncias com base em seus requisitos de segurança.

#### 2. Pares de Chaves:

Pares de chaves são usados para se conectar com segurança às suas instâncias EC2 usando SSH (Secure Shell) ou RDP (Remote Desktop Protocol) para instâncias Windows. Um par de chaves consiste em uma chave pública e uma chave privada. Aqui está como os pares de chaves funcionam:

- **Chave Pública:** A chave pública é armazenada na instância EC2 e é usada pela instância para autenticar conexões SSH ou RDP. Ela também é usada para criptografar dados que só podem ser descriptografados com a chave privada correspondente.
- **Chave Privada:** A chave privada é armazenada com segurança em sua máquina local e é usada para autenticar sua identidade ao se conectar à instância EC2. Ela deve ser mantida confidencial e não deve ser compartilhada com ninguém.
- **Criação de Pares de Chaves:** Quando você lança uma nova instância EC2, tem a opção de especificar um par de chaves existente ou criar um novo. Se você criar um novo par de chaves, a AWS gerará um par de chaves público/privado para você, e você será solicitado a baixar o arquivo da chave privada. É importante manter este arquivo de chave privada seguro e não expô-lo a usuários não autorizados.
- **Autenticação SSH:** Quando você se conecta à sua instância EC2 via SSH, você especifica o caminho para o arquivo da chave privada usando a flag ‘-i’. O cliente SSH usa a chave privada para autenticar sua identidade à instância EC2.

### Exemplos de Código para Lançamento de Instâncias EC2 usando AWS CLI

Lançando uma instância EC2 usando AWS CLI:

```sh
aws ec2 run-instances \
    --image-id ami-12345678 \
    --instance-type t2.micro \
    --key-name MyKeyPair \
    --security-groups MySecurityGroup \
    --subnet-id subnet-12345678
```

Neste exemplo:

- `image-id`: Especifica o ID da Imagem de Máquina Amazon (AMI).
- `instance-type`: Especifica o tipo de instância.
- `key-name`: Especifica o nome do par de chaves usado para se conectar à instância.
- `security-groups`: Especifica o(s) grupo(s) de segurança associado(s) à instância.
- `subnet-id`: Especifica a sub-rede na qual lançar a instância.

### Exemplos de Código para Gerenciamento de Grupos de Segurança:

Criando um grupo de segurança:

```sh
aws ec2 create-security-group \
    --group-name MySecurityGroup \
    --description "My Security Group"
```

Adicionando regras de entrada para permitir tráfego SSH (porta 22) e HTTP (porta 80):

```sh
aws ec2 authorize-security-group-ingress \
    --group-name MySecurityGroup \
    --protocol tcp \
    --port 22 \
    --cidr 0.0.0.0/0

aws ec2 authorize-security-group-ingress \
    --group-name MySecurityGroup \
    --protocol tcp \
    --port 80 \
    --cidr 0.0.0.0/0
```

### Exemplos de Código para Gerenciamento de Pares de Chaves:

Criando um novo par de chaves:

```sh
aws ec2 create-key-pair \
    --key-name MyKeyPair \
    --query 'KeyMaterial' \
    --output text > MyKeyPair.pem
```

O comando criará um novo par de chaves chamado ‘MyKeyPair’ e salvará a chave privada em um arquivo chamado ‘MyKeyPair.pem’.

Descrevendo pares de chaves existentes:

```sh
aws ec2 describe-key-pairs
```

Deletando um par de chaves:

```sh
aws ec2 delete-key-pair --key-name MyKeyPair
```

### Questões de Entrevista Baseadas em Cenários para Engenheiros DevOps Focando em Instâncias EC2, Grupos de Segurança e Pares de Chaves

#### Cenário: Você foi encarregado de otimizar o custo das instâncias EC2 em sua organização. Como você abordaria essa tarefa?
**Resposta:** Eu consideraria implementar várias estratégias de otimização de custos, como:

- Utilizar Instâncias Reservadas da AWS para instâncias com padrões de uso previsíveis.
- Implementar Auto Scaling para ajustar dinamicamente o número de instâncias com base na demanda.
- Aproveitar Instâncias Spot do EC2 para cargas de trabalho não críticas e tolerantes a falhas para aproveitar a capacidade ociosa a custos mais baixos.

#### Cenário: Uma de suas aplicações hospedadas em instâncias EC2 está experimentando degradação de desempenho. Como você solucionaria e resolveria esse problema?
**Resposta:** Eu começaria investigando vários fatores que poderiam contribuir para a degradação de desempenho, incluindo:

- Monitoramento de métricas de CPU, memória, I/O de disco e rede usando Amazon CloudWatch.
- Revisão de logs e métricas de aplicação para identificar quaisquer erros ou gargalos.
- Análise da utilização de recursos dentro das instâncias EC2 e escalando os recursos se necessário.
- Otimização do código da aplicação e das configurações para melhorar o desempenho.
- Consideração de upgrades de tipo de instância ou uso de recursos de rede aprimorados para desempenho melhorado.

#### Cenário: Você precisa garantir que apenas endereços IP específicos tenham acesso às suas instâncias EC2. Como você configuraria grupos de segurança para impor essa restrição?
**Resposta:** Eu criaria um novo grupo de segurança e definiria regras de entrada para permitir tráfego apenas dos endereços IP ou blocos CIDR especificados. Por exemplo:

- Permitir acesso SSH (porta 22) apenas de um intervalo específico de endereços IP.
- Permitir acesso HTTP/HTTPS (portas 80 e 443) apenas de fontes conhecidas.
- Negar todo o outro tráfego de entrada para restringir ainda mais o acesso.

#### Cenário: Sua equipe está implantando uma nova aplicação web em instâncias EC2 que requer acesso a um servidor de banco de dados externo. Como você configuraria grupos de segurança para permitir a comunicação entre os servidores de aplicação e o servidor de banco de dados?
**Resposta:** Eu criaria grupos de segurança separados para os servidores de aplicação e para o servidor de banco de dados. Em seguida, eu configuraria regras de entrada para o grupo de segurança dos servidores de aplicação para permitir tráfego nas portas necessárias do banco de dados (por exemplo, porta 3306 para MySQL) do grupo de segurança dos servidores de aplicação. Da mesma forma, eu configuraria regras de saída para o grupo de segurança do servidor de banco de dados para permitir tráfego dos servidores de aplicação.

#### Cenário: Você precisa acessar suas instâncias EC2 com segurança via SSH. Como você gerenciaria pares de chaves SSH para autenticação?
**Resposta:** Eu geraria um novo par de chaves SSH usando ferramentas como ssh-keygen e armazenaria a chave privada com segurança em minha máquina local. Em seguida, eu carregaria a chave pública na AWS e a associaria às instâncias EC2 durante a criação da instância. Além disso, eu garantiria que apenas usuários autorizados tenham acesso à chave privada e rotacionaria regularmente as chaves SSH para melhorar a segurança.

#### Cenário: Você perdeu o acesso a uma instância EC2 porque perdeu a chave privada. Como você recuperaria o acesso à instância?
**Resposta:** Se eu perdesse o acesso à chave privada, eu tentaria recuperar o acesso através do Console de Gerenciamento da AWS da seguinte forma:

- Criando um novo par de chaves.
- Associando o novo par de chaves à instância EC2.
- Parando a instância (se possível).
- Desanexando o volume root da instância.
- Anexando

o volume root a uma nova instância temporária.
- Montando o volume root da instância temporária e modificando a configuração SSH para permitir acesso com o novo par de chaves.
- Desanexando o volume root da instância temporária e reanexando-o à instância original.
- Iniciando a instância e acessando-a com o novo par de chaves.

### Conclusão

Parabéns! Você lançou com sucesso sua primeira instância EC2 e ganhou insights sobre grupos de segurança e pares de chaves. Fique ligado para a exploração de amanhã em mais serviços da AWS.

Isso é tudo para o Dia 3 de nossa jornada na AWS. Feliz computação em nuvem!
