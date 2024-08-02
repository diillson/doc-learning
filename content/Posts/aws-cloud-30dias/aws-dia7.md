---
title: "Dia 7: VPC (Virtual Private Cloud)"
date: 2024-08-04
description: "Exprore o VPC (Virtual Private Cloud), um componente fundamental da infraestrutura da Amazon Web Services. Descubra como criar VPCs personalizados, configurar tabelas de roteamento e conectar redes usando peering e VPN."
tags: ["AWS", "VPC", "Cloud", "Networking"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia7"]
author: ["Edilson Freitas"]
cover:
  image: images/vpc.jpg
  hiddenInList: true
---

## Bem-vindo ao Dia 7 do nosso curso de 30 dias sobre AWS!

Hoje, mergulhamos no mundo do Virtual Private Cloud (VPC), um bloco de construção fundamental da infraestrutura da Amazon Web Services. O VPC permite criar uma seção logicamente isolada da nuvem AWS onde você pode iniciar recursos da AWS em uma rede virtual que você define.

## Compreendendo os Conceitos de VPC

É essencial entender os conceitos de VPC para projetar e gerenciar sua infraestrutura AWS de maneira eficaz. Vamos explorar cada um desses conceitos em detalhes:

### 1. Sub-redes (Subnets)

As sub-redes são segmentos de endereços IP dentro do seu VPC que permitem particionar logicamente sua rede. Pontos chave sobre sub-redes incluem:

- **Blocos CIDR**: Cada sub-rede está associada a um bloco CIDR (Classless Inter-Domain Routing) específico, que define o intervalo de endereços IP disponíveis dentro dessa sub-rede.
- **Zonas de Disponibilidade (AZs)**: As sub-redes são implantadas em zonas de disponibilidade específicas. Uma zona de disponibilidade é um local distinto dentro de uma região AWS, proporcionando alta disponibilidade e tolerância a falhas.
- **Sub-redes Públicas e Privadas**: Você pode designar sub-redes como públicas ou privadas com base em sua acessibilidade à internet. Sub-redes públicas normalmente têm uma rota para um gateway de internet, enquanto sub-redes privadas não.

### 2. Tabelas de Roteamento (Route Tables)

As tabelas de roteamento controlam o tráfego de rede dentro do seu VPC. Pontos chave sobre tabelas de roteamento incluem:

- **Tabela de Roteamento Padrão**: Quando você cria um VPC, uma tabela de roteamento padrão é criada automaticamente. Sub-redes que não estão explicitamente associadas a uma tabela de roteamento personalizada são associadas a esta tabela padrão.
- **Tabelas de Roteamento Personalizadas**: Você pode criar tabelas de roteamento personalizadas para definir regras de roteamento específicas para suas sub-redes. Por exemplo, você pode configurar uma tabela de roteamento personalizada para sub-redes públicas para rotear o tráfego destinado à internet para um gateway de internet.
- **Rotas**: Cada tabela de roteamento contém um conjunto de rotas que determinam para onde o tráfego de rede deve ser direcionado. Essas rotas especificam os blocos CIDR de destino e o alvo para o tráfego, como um gateway de internet ou um gateway privado virtual para conexões VPN.

### 3. Gateways de Internet (Internet Gateways)

Um gateway de internet (IGW) facilita a comunicação entre instâncias dentro do seu VPC e a internet. Pontos chave sobre gateways de internet incluem:

- **Comunicação Bidirecional**: Um gateway de internet permite que instâncias dentro do seu VPC se comuniquem com recursos fora do VPC e vice-versa.
- **Associado a um VPC**: Um gateway de internet é associado a um VPC específico e serve como um alvo na tabela de roteamento do VPC para tráfego destinado à internet.
- **Controle de Acesso**: Por padrão, recursos dentro de um VPC não podem se comunicar com a internet. Você deve configurar as tabelas de roteamento das suas sub-redes para rotear o tráfego destinado à internet para o gateway de internet.

## Criando VPCs e Sub-redes Personalizadas

Criar VPCs e sub-redes personalizadas na AWS permite ajustar sua infraestrutura de rede para as necessidades específicas de seus aplicativos e serviços. Aqui está um guia passo a passo para criar VPCs e sub-redes personalizadas:

### Criando VPCs Personalizadas

1. **Navegue até o Painel do VPC**:
   Faça login no Console de Gerenciamento da AWS e navegue até o painel do VPC.

2. **Inicie o Assistente de Criação de VPC**:
   Clique no botão “Criar VPC” e você será solicitado a inserir os detalhes para sua nova VPC.

3. **Digite os Detalhes da VPC**:
   - Forneça um nome para sua VPC.
   - Especifique o bloco CIDR IPv4 para sua VPC. Isso define o intervalo de endereços IP que podem ser usados dentro da sua VPC. Escolha um bloco CIDR que não sobreponha nenhum bloco CIDR existente em sua conta AWS.

4. **Configure Configurações Opcionais**:
   - Você pode opcionalmente configurar configurações como bloco CIDR IPv6, resolução DNS, nomes DNS e locação (padrão ou dedicada). Escolha opções de acordo com seus requisitos.

5. **Crie a VPC**:
   - Revise as configurações que você configurou.
   - Clique no botão “Criar VPC” para criar sua VPC personalizada.

### Criando Sub-redes Dentro da VPC Personalizada

1. **Navegue até a Seção de Sub-redes**:
   Depois que sua VPC for criada, navegue até a seção “Sub-redes” no painel do VPC.

2. **Inicie o Assistente de Criação de Sub-rede**:
   Clique no botão “Criar Sub-rede”.

3. **Digite os Detalhes da Sub-rede**:
   - Selecione a VPC que você criou anteriormente.
   - Forneça um nome para sua sub-rede.
   - Especifique o bloco CIDR IPv4 para a sub-rede. Esse bloco CIDR deve ser um subconjunto do bloco CIDR da sua VPC.

4. **Selecione a Zona de Disponibilidade**:
   - Escolha a Zona de Disponibilidade onde você deseja implantar sua sub-rede. Lembre-se de que cada sub-rede reside em uma Zona de Disponibilidade.

5. **Configure a Associação da Tabela de Roteamento**:
   - Especifique a tabela de roteamento que você deseja associar à sub-rede. Por padrão, as sub-redes estão associadas à tabela de roteamento principal da VPC. No entanto, você pode criar tabelas de roteamento personalizadas e associá-las a sub-redes específicas.

6. **Crie a Sub-rede**:
   - Revise a configuração da sub-rede.
   - Clique no botão “Criar Sub-rede” para criar sua sub-rede.

## Configurando Peering de VPC e Conexões VPN

Esses são recursos avançados de rede na AWS que permitem comunicação entre diferentes VPCs e entre sua rede local e sua infraestrutura AWS, respectivamente. Vamos explorar cada um desses conceitos:

### 1. Peering de VPC

O peering de VPC permite conectar duas VPCs dentro da mesma região AWS, permitindo que instâncias em uma VPC se comuniquem com instâncias na outra VPC usando endereços IP privados. Veja como configurar o peering de VPC:

1. **Navegue até o Painel do VPC**:
   Faça login no Console de Gerenciamento da AWS e navegue até o painel do VPC.

2. **Inicie o Assistente de Conexão de Peering**:
   No painel do VPC, clique em “Conexões de Peering” na barra lateral e clique no botão “Criar Conexão de Peering”.

3. **Digite os Detalhes da Conexão de Peering**:
   - Especifique um nome para a conexão de peering.
   - Selecione a VPC com a qual você deseja estabelecer o peering.
   - Insira o ID da conta AWS do proprietário da outra VPC.
   - Selecione a outra VPC com a qual você deseja fazer peering.

4. **Envie o Pedido de Conexão de Peering**:
   Depois de configurar os detalhes da conexão de peering, clique no botão “Criar Conexão de Peering”. A conexão de peering ficará em estado pendente até que o proprietário da outra VPC aceite o pedido de peering.

5. **Aceite a Conexão de Peering (No Outro Lado da VPC)**:
   O proprietário da outra VPC deve navegar até a seção “Conexões de Peering” no painel do VPC e aceitar o pedido de peering.

6. **Atualize as Tabelas de Roteamento**:
   Depois que a conexão de peering for estabelecida, atualize as tabelas de roteamento das VPCs respectivas para rotear o tráfego destinado ao bloco CIDR da outra VPC através da conexão de peering.

### 2. Conexões VPN

Conexões VPN permitem estabelecer conexões seguras entre sua rede local e sua infraestrutura AWS, permitindo estender seu data center para a nuvem. Veja como configurar conexões VPN:

1. **Gateway Virtual Privado (VGW)**:
   -

 Crie um gateway virtual privado e anexe-o à sua VPC. Este gateway atua como o ponto final VPN no lado da AWS.

2. **Gateway de Cliente (CGW)**:
   - Crie um gateway de cliente representando seu dispositivo VPN local. Especifique o endereço IP público do seu dispositivo VPN local e as informações de roteamento.

3. **Conexão VPN**:
   - Crie uma conexão VPN entre o gateway virtual privado e o gateway de cliente. Configure o método de autenticação, algoritmo de criptografia e outras configurações de acordo com seus requisitos.

4. **Baixe a Configuração**:
   - Baixe a configuração VPN fornecida pela AWS, que inclui as configurações necessárias para seu dispositivo VPN local.

5. **Configure o Dispositivo VPN Local**:
   - Configure seu dispositivo VPN local usando a configuração baixada e estabeleça a conexão VPN entre sua rede local e sua VPC.

6. **Atualize as Tabelas de Roteamento**:
   - Atualize as tabelas de roteamento das suas sub-redes para rotear o tráfego destinado à sua rede local através da conexão VPN.

## Exemplos de Código com AWS SDK para Python (Boto3)

### Criando VPC Personalizada

```python
import boto3

# Criar uma VPC
ec2_client = boto3.client('ec2')

response = ec2_client.create_vpc(
    CidrBlock='10.0.0.0/16',
    AmazonProvidedIpv6CidrBlock=False
)

vpc_id = response['Vpc']['VpcId']
print("VPC criada com ID:", vpc_id)
```

### Criando Sub-redes Dentro da VPC Personalizada

```python
# Criar uma Sub-rede
response = ec2_client.create_subnet(
    VpcId=vpc_id,
    CidrBlock='10.0.1.0/24',
    AvailabilityZone='us-east-1a'
)

subnet_id = response['Subnet']['SubnetId']
print("Sub-rede criada com ID:", subnet_id)
```

### Configurando Peering de VPC

```python
# Criar uma Conexão de Peering
response = ec2_client.create_vpc_peering_connection(
    VpcId=vpc_id,
    PeerVpcId='peer-vpc-id'
)

peering_connection_id = response['VpcPeeringConnection']['VpcPeeringConnectionId']
print("Conexão de peering criada com ID:", peering_connection_id)
```

### Aceitando Conexão de Peering (do Outro Lado da VPC)

```python
# Aceitar Conexão de Peering (no outro lado da VPC)
response = ec2_client.accept_vpc_peering_connection(
    VpcPeeringConnectionId='peering-connection-id'
)
```

### Configurando Conexão VPN

```python
# Criar um Gateway Virtual Privado
response = ec2_client.create_vpn_gateway(
    Type='ipsec.1'
)

vgw_id = response['VpnGateway']['VpnGatewayId']
print("Gateway Virtual Privado criado com ID:", vgw_id)

# Criar um Gateway de Cliente
response = ec2_client.create_customer_gateway(
    Type='ipsec.1',
    PublicIp='customer-gateway-public-ip',
    BgpAsn=65000
)

cgw_id = response['CustomerGateway']['CustomerGatewayId']
print("Gateway de Cliente criado com ID:", cgw_id)

# Criar uma Conexão VPN
response = ec2_client.create_vpn_connection(
    CustomerGatewayId=cgw_id,
    VpnGatewayId=vgw_id,
    Options={
        'StaticRoutesOnly': True
    }
)

vpn_connection_id = response['VpnConnection']['VpnConnectionId']
print("Conexão VPN criada com ID:", vpn_connection_id)
```

## Perguntas e Respostas Baseadas em Cenários

### Cenário: Sua empresa está implantando um aplicativo multi-tier que inclui servidores web, servidores de aplicativos e servidores de banco de dados. Como você projetaria a VPC e as sub-redes para garantir segurança e alta disponibilidade para cada camada?

**Resposta**:
- Eu projetaria a VPC com sub-redes separadas para cada camada, como sub-redes públicas para servidores web, sub-redes privadas para servidores de aplicativos e sub-redes isoladas para servidores de banco de dados.
- Cada sub-rede teria configurações apropriadas de grupos de segurança para controlar o tráfego de entrada e saída com base no princípio do menor privilégio.
- Também distribuiria as sub-redes em várias Zonas de Disponibilidade para garantir alta disponibilidade e tolerância a falhas.

### Cenário: Sua empresa adquiriu outra empresa com sua própria infraestrutura AWS. Como você integraria as duas VPCs usando o peering de VPC, mantendo segurança e conformidade?

**Resposta**:
- Eu estabeleceria conexões de peering de VPC entre as VPCs das duas empresas, garantindo que os blocos CIDR não se sobreponham.
- Após o estabelecimento das conexões de peering, revisaria e atualizaria as tabelas de roteamento para permitir o fluxo de tráfego entre as VPCs pareadas, mantendo políticas de segurança e requisitos de conformidade.
- Também garantiria que qualquer resolução DNS e configurações de lista de controle de acesso à rede (NACL) necessárias estivessem em vigor.

### Cenário: A equipe de desenvolvimento da sua empresa precisa de acesso seguro aos recursos na VPC AWS a partir de locais remotos. Como você configuraria uma conexão VPN para facilitar isso?

**Resposta**:
- Eu configuraria uma conexão VPN entre os locais remotos e a VPC AWS usando configurações de gateway virtual privado (VGW) e gateway de cliente (CGW).
- Cada local remoto teria seu próprio CGW representando seu dispositivo VPN, e a VPC AWS teria um VGW.
- Configuraria as definições da conexão VPN, incluindo algoritmos de criptografia, chaves compartilhadas e opções de túnel, para garantir comunicação segura.
- Após estabelecer a conexão VPN, atualizaria as tabelas de roteamento da VPC para rotear o tráfego entre a VPC e os locais remotos através da conexão VPN.

### Cenário: Sua empresa está enfrentando problemas de conectividade com a internet para instâncias em uma sub-rede específica dentro da VPC. Como você solucionaria e resolveria o problema relacionado a tabelas de roteamento e gateways de internet?

**Resposta**:
- Primeiro, verificaria se a tabela de roteamento da sub-rede tem uma rota padrão (0.0.0.0/0) apontando para o gateway de internet.
- Checaria a anexação do gateway de internet para garantir que ele esteja corretamente associado à VPC.
- Se as configurações da tabela de roteamento e do gateway de internet parecerem corretas, investigaria listas de controle de acesso à rede (NACLs) e configurações de grupo de segurança para garantir que não estejam bloqueando o tráfego de saída.
- Além disso, verificaria qualquer configuração de tradução de endereço de rede (NAT) se as instâncias estiverem em sub-redes privadas.

## Conclusão

Hoje, cobrimos o essencial do Virtual Private Cloud na AWS. À medida que você continua sua jornada na AWS, lembre-se de experimentar diferentes configurações e mantenha a curiosidade sobre as possibilidades que o VPC oferece na construção de infraestruturas robustas e seguras na nuvem.

Fique atento para a sessão de amanhã, onde exploraremos o Auto Scaling na AWS!