---
title: "Dia 18: Melhores Práticas de Segurança"
date: "2024-08-23"
description: "A AWS oferece um conjunto robusto de ferramentas e recursos para ajudá-lo a proteger sua infraestrutura."
categories: ["Cloud"]
tags: ["AWS Security", "SecAws", "iam", "developement"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia18"]
author: ["Edilson Freitas"]
cover:
  image: images/sec.png
  hiddenInList: true
---

## Bem-vindo ao Dia 18 do nosso curso de 30 dias sobre AWS! 

Hoje, estamos mergulhando em um dos aspectos mais críticos da computação em nuvem: a segurança. 

A AWS oferece um conjunto robusto de ferramentas e recursos para ajudá-lo a proteger sua infraestrutura, mas é essencial entender o modelo de responsabilidade compartilhada e implementar as melhores práticas para garantir a segurança dos seus dados e aplicações.

### Entendendo o Modelo de Responsabilidade Compartilhada da AWS:

O Modelo de Responsabilidade Compartilhada da AWS é um conceito fundamental para quem trabalha com serviços da AWS. Ele define as responsabilidades tanto da AWS quanto do cliente em relação à segurança e conformidade. Entender esse modelo é crucial para proteger efetivamente suas aplicações e dados na nuvem AWS.

#### Responsabilidades da AWS:

- **Segurança da Infraestrutura:** A AWS é responsável pela segurança da infraestrutura global que executa todos os serviços da AWS. Isso inclui a segurança física dos data centers, redes e infraestrutura de hardware.
- **Manutenção de Hardware e Software:** A AWS gerencia a manutenção e as atualizações dos componentes de hardware e software subjacentes necessários para entregar os serviços da AWS.
- **Programas de Conformidade Global:** A AWS mantém vários programas e certificações de conformidade para garantir a segurança e conformidade de sua infraestrutura. Isso inclui certificações como ISO 27001, SOC 1/2/3, PCI DSS e HIPAA.
- **Serviços Gerenciados:** A AWS oferece serviços gerenciados como Amazon RDS, Amazon DynamoDB e AWS Lambda, onde a AWS cuida dos aspectos operacionais, incluindo patches de segurança e atualizações.

#### Responsabilidades do Cliente:

- **Segurança dos Dados:** Os clientes são responsáveis por proteger seus dados, incluindo criptografia, controle de acesso e integridade dos dados. Isso envolve selecionar métodos de criptografia apropriados e gerenciar as chaves de criptografia com segurança.
- **Segurança da Plataforma:** Os clientes são responsáveis por proteger suas aplicações, sistemas operacionais e configurações de rede que rodam na AWS. Isso inclui aplicar patches ao sistema operacional, configurar firewalls e implementar as melhores práticas de segurança.
- **Gerenciamento de Identidade e Acesso (IAM):** Os clientes são responsáveis por gerenciar o acesso dos usuários aos serviços e recursos da AWS. Isso envolve criar usuários, grupos, funções e políticas IAM, garantindo o princípio do menor privilégio.
- **Conformidade:** Os clientes são responsáveis por garantir a conformidade com as leis, regulamentos e padrões da indústria aplicáveis. Isso inclui implementar controles de segurança e monitorar a conformidade.

#### Responsabilidades Compartilhadas em Ação:

- **Exemplo 1 — Amazon S3:** A AWS é responsável por proteger a infraestrutura subjacente do Amazon S3, incluindo a segurança dos data centers e a proteção da rede. No entanto, os clientes são responsáveis por configurar políticas de controle de acesso, configurações de criptografia e gerenciar os dados armazenados em buckets S3.
- **Exemplo 2 — Amazon EC2:** A AWS é responsável por proteger os hosts físicos que executam as instâncias EC2, bem como o hipervisor. Os clientes são responsáveis por proteger suas instâncias EC2 aplicando atualizações de segurança, configurando firewalls e implementando grupos de segurança.

### Implementando as Melhores Práticas de Segurança para IAM, S3 e EC2:

A segurança é primordial ao trabalhar com serviços da AWS, como Identity and Access Management (IAM), Simple Storage Service (S3) e Elastic Compute Cloud (EC2). Implementar as melhores práticas garante que seus recursos e dados permaneçam seguros contra acessos não autorizados ou violações. Vamos explorar algumas das principais práticas recomendadas para cada serviço:

#### IAM (Identity and Access Management):

1. **Use Controle de Acesso Baseado em Funções (RBAC):**

    - Atribua permissões aos usuários IAM com base em suas funções na organização.
    - Evite usar as credenciais da conta root para tarefas rotineiras.

2. **Implemente o Princípio do Menor Privilégio:**

    - Atribua apenas as permissões necessárias para que os usuários executem suas tarefas.
    - Revise e refine regularmente as permissões para remover acessos desnecessários.

3. **Ative a Autenticação Multifator (MFA):**

    - Exija que os usuários se autentiquem com uma segunda forma de verificação, como um dispositivo móvel ou token de hardware.
    - Ative a MFA para contas privilegiadas e usuários IAM com acesso a dados sensíveis.

4. **Gire Credenciais Regularmente:**

    - Gire chaves de acesso, senhas e chaves secretas periodicamente para mitigar o risco de acesso não autorizado devido a credenciais comprometidas.

#### S3 (Simple Storage Service):

1. **Controle de Acesso Seguro:**

    - Use políticas de bucket e listas de controle de acesso (ACLs) para gerenciar o acesso a buckets e objetos S3.
    - Siga o princípio do menor privilégio ao definir permissões de acesso.

2. **Criptografe os Dados:**

    - Ative a criptografia no lado do servidor para criptografar dados em repouso usando AWS Key Management Service (KMS) ou chaves de criptografia gerenciadas pela Amazon S3.
    - Use criptografia no lado do cliente para criptografar dados antes de fazer upload para o S3.

3. **Implemente o Versionamento:**

    - Ative o versionamento em buckets S3 para manter várias versões de objetos e proteger contra exclusões ou modificações acidentais.

4. **Monitore e Audite o Acesso:**

    - Ative o AWS CloudTrail para registrar chamadas de API do S3 e rastrear o acesso a buckets e objetos.
    - Configure o log de acesso do Amazon S3 para registrar as solicitações feitas aos buckets e objetos S3 para fins de auditoria.

#### EC2 (Elastic Compute Cloud):

1. **Grupos de Segurança e ACLs de Rede:**

    - Use grupos de segurança para controlar o tráfego de entrada e saída para instâncias EC2 no nível da instância.
    - Utilize ACLs de rede para controlar o tráfego no nível do subnet.

2. **Gerenciamento de Patches:**

    - Mantenha as instâncias EC2 atualizadas com os patches de segurança mais recentes para mitigar vulnerabilidades.
    - Implemente soluções automatizadas de gerenciamento de patches para agilizar o processo de aplicação de patches.

3. **Isolamento de Instâncias:**

    - Implemente o isolamento de instâncias executando diferentes tipos de workloads em instâncias EC2 separadas.
    - Utilize AWS VPC (Virtual Private Cloud) para isolar instâncias em redes logicamente separadas.

4. **Endurecimento de Instâncias:**

    - Desative serviços e protocolos desnecessários nas instâncias EC2 para reduzir a superfície de ataque.
    - Configure mecanismos de autenticação fortes e aplique políticas de senha.

### Configurando Criptografia, Controles de Acesso e Auditoria:

#### Criptografia:

1. **Criptografia no Lado do Servidor (SSE):**

    - Utilize AWS Key Management Service (KMS) ou chaves gerenciadas pela Amazon S3 para ativar a criptografia no lado do servidor para buckets S3.
    - Criptografe volumes Amazon EBS usando chaves gerenciadas pela AWS, chaves gerenciadas pelo cliente ou chaves fornecidas pelo cliente (SSE-S3, SSE-KMS ou SSE-C).

2. **Criptografia no Lado do Cliente:**

    - Criptografe dados antes de fazer upload para o Amazon S3 usando bibliotecas de criptografia no lado do cliente ou SDKs da AWS.
    - Implemente criptografia no nível da aplicação antes de armazenar dados sensíveis no Amazon RDS ou DynamoDB.

3. **Criptografia da Camada de Transporte:**

    - Ative SSL/TLS para criptografar dados em trânsito entre clientes e serviços da AWS, como Amazon API Gateway, AWS Elastic Beanstalk e Amazon CloudFront.

#### Controles de Acesso:

1. **Políticas IAM:**

    - Defina políticas IAM granulares para controlar o acesso a serviços e recursos da AWS.
    - Use condições nas políticas IAM para aplicar controles de acesso adicionais com base em fatores como endereços IP, horário do dia ou status de autenticação multifator (MFA).

2. **Políticas Baseadas em Recursos:**

    - Configure políticas baseadas em recursos para serviços como Amazon S3 e Amazon SQS para controlar o acesso no nível do recurso.
    - Especifique quem pode acessar recursos específicos e quais ações eles podem realizar usando políticas baseadas em JSON.

3. **Políticas de Bucket:**

    - Crie políticas de bucket para buckets Amazon S3 para definir permissões de acesso no nível do bucket.
    - Restrinja o acesso com base em endereços IP, IDs de contas AWS ou outras condições para evitar acesso não autorizado.

#### Auditoria:

1. **AWS CloudTrail:**

    - Ative o AWS CloudTrail para registrar chamadas de API e monitorar atividades em toda a sua infraestrutura AWS.
    - Configure o CloudTrail para entregar arquivos de log ao Amazon S3 ou Amazon CloudWatch Logs para armazenamento e análise.

2. **Amazon CloudWatch Logs:**

    - Use

o Amazon CloudWatch Logs para centralizar e monitorar dados de log de vários serviços da AWS.
- Configure alarmes e notificações para alertá-lo sobre atividades suspeitas ou eventos de segurança.

3. **AWS Config:**

    - Ative o AWS Config para avaliar, auditar e monitorar as configurações dos seus recursos AWS.
    - Use regras do AWS Config para aplicar conformidade com melhores práticas de segurança e padrões da indústria.

4. **Amazon GuardDuty:**

    - Ative o Amazon GuardDuty para monitorar e detectar ameaças continuamente no seu ambiente AWS.
    - Receba alertas para achados relacionados a acesso não autorizado, atividade maliciosa ou comportamento incomum.

### Perguntas de Entrevista Baseadas em Cenários:

Aqui estão algumas perguntas de entrevista baseadas em cenários, juntamente com respostas exemplares, que cobrem os tópicos de criptografia, controles de acesso e auditoria na AWS:

**Cenário 1 — Sua equipe está migrando dados sensíveis de clientes para o Amazon S3. Como você garantiria a segurança desses dados em repouso?**  
**Resposta:** Para garantir a segurança dos dados sensíveis em repouso no Amazon S3, eu habilitaria a criptografia no lado do servidor (SSE) usando o AWS Key Management Service (KMS) ou chaves gerenciadas pela Amazon S3. Isso garante que todos os objetos armazenados no bucket S3 estejam criptografados, proporcionando uma camada adicional de proteção contra acesso não autorizado ou violações de dados. Além disso, configuraria políticas de bucket S3 para impor requisitos de criptografia e evitar que os dados sejam armazenados de forma não criptografada.

**Cenário 2 — Sua aplicação precisa se comunicar de forma segura com uma API de terceiros hospedada na AWS. Como você garantiria a integridade dos dados durante o trânsito?**  
**Resposta:** Para garantir a integridade dos dados durante o trânsito entre nossa aplicação e a API de terceiros hospedada na AWS, eu utilizaria o protocolo HTTPS para comunicação. Criptografando os dados usando SSL/TLS, podemos prevenir a alteração ou interceptação dos dados durante o trânsito. Além disso, eu verificaria o certificado SSL da API de terceiros para garantir uma conexão segura e mitigar o risco de ataques do tipo "man-in-the-middle".

**Cenário 3 — Sua organização opera várias contas AWS para diferentes departamentos. Como você implementaria o gerenciamento centralizado de acesso entre essas contas?**  
**Resposta:** Para implementar o gerenciamento centralizado de acesso entre várias contas AWS, eu usaria o AWS Organizations. Criando uma organização com faturamento consolidado, posso gerenciar e governar centralmente as políticas de controle de acesso, como funções e permissões IAM, em todas as contas membros. Isso permite o acesso e compartilhamento de recursos de forma contínua, mantendo o controle granular sobre permissões e requisitos de conformidade.

**Cenário 4 — Sua equipe precisa conceder acesso temporário a um contratante externo para um projeto específico. Como você gerenciaria de forma segura o acesso dele aos recursos da AWS?**  
**Resposta:** Para gerenciar de forma segura o acesso temporário de um contratante externo, eu criaria uma função IAM com permissões limitadas, adaptadas aos requisitos do projeto. Usando a Federação de Identidade da AWS, posso conceder credenciais temporárias ao contratante, permitindo que ele assuma a função IAM e acesse os recursos AWS necessários. Além disso, eu implementaria a autenticação multifator (MFA) para aumentar a segurança e garantir que apenas usuários autorizados possam acessar o ambiente AWS.

**Cenário 5 — Sua organização precisa rastrear as mudanças feitas nos recursos críticos de infraestrutura na AWS. Como você configuraria a auditoria para alcançar isso?**  
**Resposta:** Para rastrear as mudanças feitas nos recursos críticos de infraestrutura na AWS, eu ativaria o AWS Config. Configurando regras do AWS Config, posso monitorar e registrar mudanças nas configurações dos recursos, como instâncias EC2, buckets S3 e grupos de segurança. O AWS Config registra essas mudanças e oferece visibilidade do histórico de configuração dos recursos, permitindo que auditemos e solucionemos quaisquer modificações não autorizadas ou violações de conformidade.

**Cenário 6 — Sua equipe precisa investigar um incidente de segurança envolvendo acesso não autorizado a uma instância EC2. Como você usaria o AWS CloudTrail para auxiliar na investigação?**  
**Resposta:** Para investigar um incidente de segurança envolvendo acesso não autorizado a uma instância EC2, eu usaria o AWS CloudTrail para revisar as chamadas de API e ações realizadas por usuários ou entidades no nosso ambiente AWS. Analisando os logs do CloudTrail, posso identificar a origem do acesso não autorizado, rastrear as atividades realizadas na instância EC2 comprometida e determinar a extensão da violação de segurança. Além disso, eu usaria o CloudTrail Insights para detectar e alertar automaticamente sobre atividades suspeitas, permitindo uma resposta proativa a incidentes de segurança.

### Conclusão:

A segurança é primordial na nuvem, e a AWS oferece uma ampla gama de ferramentas e recursos para ajudá-lo a implementar medidas de segurança robustas. Entendendo o modelo de responsabilidade compartilhada e seguindo as melhores práticas de segurança para IAM, S3 e EC2, você pode criar um ambiente seguro e em conformidade para suas aplicações e dados na AWS.

Fique atento para o Dia 19, onde exploraremos a otimização de custos na AWS! Até lá!