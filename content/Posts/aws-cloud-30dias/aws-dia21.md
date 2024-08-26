---
title: "Dia 21: Rede e Segurança"
date: "2024-08-26"
description: "Implementando Melhores Práticas de Segurança"
categories: ["Cloud"]
tags: ["AWS", "segurançaAWS", "AWSSecurity"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia21"]
author: ["Edilson Freitas"]
cover:
  image: images/security.jpeg
  hiddenInList: true
---

## Bem-vindo de volta à nossa jornada de 30 dias no curso da AWS! 

Hoje, vamos nos aprofundar em como fortalecer sua infraestrutura AWS com práticas robustas de rede e segurança. Garantir que sua rede esteja segura é fundamental para proteger seus dados e aplicações contra possíveis ameaças. Vamos explorar como você pode implementar as melhores práticas de segurança de rede no seu ambiente AWS.

### Implementando Melhores Práticas de Segurança de Rede

Implementar as melhores práticas de segurança de rede envolve configurar diversas medidas para proteger sua infraestrutura de rede contra acessos não autorizados, violações de dados e outras ameaças de segurança. Na AWS, você pode implementar essas práticas usando as ferramentas e serviços fornecidos pela plataforma. Vamos nos aprofundar em cada aspecto:

1. **Listas de Controle de Acesso à Rede (NACLs):**

    - As NACLs atuam como firewalls no nível do subnet, controlando o tráfego que entra e sai dos subnets em sua VPC.
    - Elas permitem definir regras para o tráfego de entrada e saída com base em endereços IP, protocolos e portas.
    - **Exemplo de Caso de Uso:** Você pode usar NACLs para restringir o acesso a subnets sensíveis, permitindo apenas que endereços IP ou faixas específicas se comuniquem com as instâncias dentro desses subnets.

2. **Grupos de Segurança:**

    - Os Grupos de Segurança atuam como firewalls virtuais para controlar o tráfego no nível da instância, permitindo ou negando o tráfego com base em regras definidas.
    - Eles são stateful, o que significa que permitem automaticamente o tráfego de retorno para solicitações iniciadas de dentro da instância.
    - **Exemplo de Caso de Uso:** Você pode usar Grupos de Segurança para permitir o tráfego de entrada apenas nas portas necessárias (por exemplo, SSH na porta 22, HTTP na porta 80) e restringir todo o outro tráfego.

3. **Web Application Firewall (WAF):**

    - O WAF ajuda a proteger suas aplicações web contra exploits comuns na web, filtrando e monitorando o tráfego HTTP.
    - Ele permite criar regras personalizáveis para bloquear ou permitir tráfego com base em condições como endereços IP, cabeçalhos HTTP ou atributos de solicitação.
    - **Exemplo de Caso de Uso:** Você pode usar o WAF para bloquear solicitações maliciosas, como ataques de injeção de SQL ou cross-site scripting (XSS), definindo regras que inspecionam cabeçalhos e cargas úteis de solicitações HTTP.

4. **Criptografia:**

    - Criptografar dados em trânsito e em repouso é crucial para manter a confidencialidade e a integridade dos dados.
    - Use serviços como o AWS Key Management Service (KMS) para gerenciar chaves de criptografia e aplicar criptografia em vários serviços da AWS.
    - **Exemplo de Caso de Uso:** Ative a criptografia para buckets do Amazon S3 para garantir que os dados armazenados neles estejam criptografados em repouso, mitigando o risco de exposição de dados em caso de acesso não autorizado.

5. **Monitoramento e Registro:**

    - Implemente mecanismos robustos de monitoramento e registro para detectar e responder a incidentes de segurança de forma eficaz.
    - Use o AWS CloudTrail para registrar chamadas de API e o AWS Config para avaliar a conformidade com políticas de segurança.
    - **Exemplo de Caso de Uso:** Configure alarmes no CloudWatch para notificá-lo sobre atividades suspeitas ou anomalias nos padrões de tráfego de rede, permitindo a detecção proativa de ameaças e a resposta.

6. **Gerenciamento de Patches:**

    - Aplique patches e atualizações regularmente aos seus recursos AWS para mitigar vulnerabilidades e riscos de segurança.
    - Utilize serviços como o AWS Systems Manager para automatizar tarefas de gerenciamento de patches em suas instâncias.
    - **Exemplo de Caso de Uso:** Agende patches automatizados para instâncias EC2 para garantir que elas estejam sempre atualizadas com os patches de segurança mais recentes.

### Configurando NACLs, Grupos de Segurança e WAF (Web Application Firewall)

Vamos nos aprofundar em cada um desses componentes:

1. **Listas de Controle de Acesso à Rede (NACLs):**

    - As NACLs são filtros de pacotes stateless que operam no nível do subnet dentro da sua Virtual Private Cloud (VPC).
    - Elas permitem que você controle o tráfego que entra e sai dos subnets, definindo regras baseadas em endereços IP, protocolos e portas.
    - Cada subnet na sua VPC deve estar associada a uma NACL, que por padrão permite todo o tráfego.
    - Quando o tráfego entra em um subnet, ele é avaliado contra as regras na NACL associada, e se corresponder a uma regra, é permitido ou negado.

**Exemplo: Configurando NACLs**

```sh
# Criando uma NACL
aws ec2 create-network-acl --vpc-id seu-vpc-id

# Adicionando regras de entrada e saída
aws ec2 create-network-acl-entry --network-acl-id seu-nacl-id --ingress --rule-number 100 --protocol tcp --port-range From=80,To=80 --cidr-block 0.0.0.0/0 --action allow
aws ec2 create-network-acl-entry --network-acl-id seu-nacl-id --egress --rule-number 100 --protocol tcp --port-range From=80,To=80 --cidr-block 0.0.0.0/0 --action allow
```

2. **Grupos de Segurança:**

    - Os Grupos de Segurança atuam como firewalls virtuais para suas instâncias, controlando o tráfego de entrada e saída com base em regras definidas.
    - Eles são stateful, permitindo automaticamente o tráfego de retorno para uma conexão iniciada de dentro da instância.
    - Grupos de Segurança podem ser associados a várias instâncias, e cada instância pode ser associada a vários Grupos de Segurança.

**Exemplo: Configurando Grupos de Segurança**

```sh
# Criando um grupo de segurança
aws ec2 create-security-group --group-name seu-grupo-seguranca --description "Descrição do seu grupo de segurança" --vpc-id seu-vpc-id

# Autorizando tráfego de entrada e saída
aws ec2 authorize-security-group-ingress --group-id seu-grupo-seguranca-id --protocol tcp --port 80 --cidr 0.0.0.0/0
aws ec2 authorize-security-group-egress --group-id seu-grupo-seguranca-id --protocol tcp --port 80 --cidr 0.0.0.0/0
```

3. **Web Application Firewall (WAF):**

    - O WAF protege suas aplicações web contra exploits comuns, filtrando e monitorando o tráfego HTTP.
    - Ele permite criar regras personalizadas para bloquear ou permitir tráfego com base em condições como endereços IP, cabeçalhos HTTP ou atributos de solicitação.
    - O WAF integra-se com outros serviços da AWS, como CloudFront, Application Load Balancer (ALB) e API Gateway.

**Exemplo: Configurando WAF**

```sh
# Criando um WebACL no WAF
aws waf create-web-acl --name seu-web-acl --default-action "allow"

# Criando regras
aws waf create-rule --name sua-regra --metric-name sua-metrica --change-token seu-change-token --region sua-regiao --statements "Statement":{"ByteMatchStatement":{"FieldToMatch":{"Type":"HEADER","Data":"Host"},"TargetString":"example.com","TextTransformations":[{"Type":"NONE"}],"PositionalConstraint":"EXACTLY"}}

# Associando regras ao WebACL
aws waf update-web-acl --web-acl-id seu-web-acl-id --change-token seu-change-token --updates "Action":"INSERT","ActivatedRule":{"Priority":1,"RuleId":"seu-rule-id","Action":{"Type":"BLOCK"}}
```

Configurando NACLs, Grupos de Segurança e WAF de acordo com os requisitos de segurança da sua organização, você pode estabelecer um mecanismo de defesa em camadas que protege seus recursos AWS contra várias ameaças e vulnerabilidades.

### Entendendo a Proteção contra DDoS e a Conectividade VPN

Entender a proteção contra DDoS e a conectividade VPN é crucial para manter uma infraestrutura de rede segura e confiável. Vamos nos aprofundar em cada um desses conceitos:

1. **Proteção contra DDoS:**

Os ataques de negação de serviço distribuído (DDoS) são tentativas maliciosas de interromper o tráfego normal de um servidor, serviço ou rede alvo, sobrecarregando-o com um grande volume de tráfego. A AWS oferece vários mecanismos de proteção contra DDoS para mitigar esses ataques:

- **AWS Shield:** O AWS Shield é um serviço de proteção DDoS gerenciado que protege aplicações web executadas na AWS. Ele fornece detecção contínua e mitigação automática em linha para minimizar o tempo de inatividade da aplicação e a latência.
- **AWS Shield Advanced:** O AWS Shield Advanced oferece proteção DDoS aprimorada para suas aplicações na AWS, com recursos adicionais, como inteligência avançada sobre ameaças e proteção contra custos de DDo

S.
- **AWS WAF (Web Application Firewall):** Embora não seja especificamente um serviço de proteção contra DDoS, o AWS WAF pode ser usado para mitigar certos tipos de ataques DDoS filtrando e monitorando o tráfego HTTP.

Os mecanismos de proteção contra DDoS na AWS são projetados para detectar e mitigar ataques em tempo real, garantindo a disponibilidade e a confiabilidade de suas aplicações mesmo sob cargas de tráfego elevadas.

2. **Conectividade VPN:**

A conectividade VPN (Virtual Private Network) permite estabelecer conexões seguras entre sua rede on-premises e sua VPC AWS. Isso possibilita a comunicação segura pela internet e estende sua rede on-premises para a nuvem AWS. A AWS oferece várias opções de conectividade VPN:

- **AWS Site-to-Site VPN:** O AWS Site-to-Site VPN permite que você conecte sua rede on-premises com segurança à sua VPC AWS pela internet, usando túneis VPN IPsec para criptografar o tráfego.
- **AWS Client VPN:** O AWS Client VPN permite que usuários individuais se conectem com segurança a recursos e serviços AWS a partir de locais remotos ou dispositivos móveis.

A conectividade VPN na AWS proporciona uma forma segura e confiável de acessar recursos em sua VPC a partir de sua rede on-premises ou de locais remotos, ajudando a proteger dados sensíveis contra acessos não autorizados e interceptações.

### Perguntas de Entrevista Baseadas em Cenários

Aqui estão algumas perguntas de entrevista baseadas em cenários e respostas focadas em tópicos como NACLs, Grupos de Segurança, WAF, proteção contra DDoS e conectividade VPN na AWS:

**Cenário:** Você foi encarregado de proteger uma aplicação web hospedada na AWS. Como você configuraria NACLs e Grupos de Segurança para proteger a aplicação enquanto permite o tráfego necessário?

**Resposta:**
- **Para NACLs:** Eu começaria criando uma NACL e associando-a aos subnets relevantes. Em seguida, configuraria regras de entrada e saída para permitir tráfego HTTP (porta 80) e HTTPS (porta 443) enquanto restrinjo o acesso a faixas de IP específicas ou blocos CIDR.
- **Para Grupos de Segurança:** Eu criaria um Grupo de Segurança e o associaria às instâncias do servidor web. Configuraria regras de entrada para permitir tráfego nas portas 80 e 443 da internet enquanto restrinjo o acesso apenas às portas e protocolos necessários. Regras de saída podem ser configuradas para permitir todo o tráfego por padrão.

**Cenário:** Sua aplicação web está enfrentando um aumento nos ataques de injeção de SQL. Como você usaria o AWS WAF para mitigar esses ataques?

**Resposta:**
- Eu começaria criando um WebACL no AWS WAF e associando-o ao CloudFront ou Application Load Balancer (ALB) que serve a aplicação web.
- Em seguida, definiria regras personalizadas no WebACL para detectar e bloquear tentativas de injeção de SQL. Essas regras inspecionariam parâmetros de solicitação HTTP em busca de padrões suspeitos indicativos de ataques de injeção de SQL.
- Monitorando e atualizando continuamente as regras do WAF, podemos efetivamente mitigar ataques de injeção de SQL e proteger a aplicação web contra essas ameaças de segurança.

**Cenário:** Sua aplicação hospedada na AWS está sendo alvo de um ataque DDoS. Como você mitigaria o ataque usando o AWS Shield?

**Resposta:**
- Primeiro, eu ativaria o AWS Shield Standard para a aplicação, que oferece proteção básica contra DDoS sem custos adicionais.
- Se o ataque persistir ou escalar, consideraria a atualização para o AWS Shield Advanced, que oferece capacidades de proteção DDoS aprimoradas e acesso ao AWS DDoS Response Team (DRT) para suporte adicional.
- Além disso, configuraria o AWS WAF para filtrar e bloquear o tráfego malicioso associado ao ataque DDoS, aumentando ainda mais a resiliência da aplicação contra essas ameaças.

**Cenário:** Sua organização exige conectividade segura entre sua rede on-premises e a AWS VPC. Como você configuraria o AWS Site-to-Site VPN para atender a esse requisito?

**Resposta:**
- Eu começaria configurando um gateway privado virtual (VGW) na VPC AWS e configurando as tabelas de roteamento apropriadas para rotear o tráfego de e para a rede on-premises através do VGW.
- Em seguida, configuraria o gateway do cliente (CGW) na rede on-premises, fornecendo as informações necessárias, como o endereço IP público do dispositivo gateway do cliente e a chave pré-compartilhada para autenticação.
- Finalmente, criaria uma conexão VPN Site-to-Site entre o VGW e o CGW, estabelecendo um túnel VPN criptografado pela internet para comunicação segura entre a rede on-premises e a AWS VPC.

### Conclusão

Rede e segurança são aspectos fundamentais de qualquer ambiente AWS. Ao implementar as melhores práticas de segurança de rede, como NACLs, Grupos de Segurança, WAF, e ao aproveitar a proteção contra DDoS e a conectividade VPN, você pode criar uma infraestrutura segura e resiliente na AWS.

Lembre-se, segurança é um processo contínuo, portanto, revise e atualize regularmente suas medidas de segurança para se adaptar a ameaças e vulnerabilidades em evolução. Fique atento para mais insights enquanto continuamos nossa jornada pela AWS!
