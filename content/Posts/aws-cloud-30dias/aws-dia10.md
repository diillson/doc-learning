---
title: "Dia 10: CloudFormation"
date: "2024-08-07"
tags: ["AWS", "CloudFormation", "IaC", "DevOps", "Infraestrutura como Código", "Cloud", "Treinamento"]
categories: ["Cloud"]
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia10"]
author: ["Edilson Freitas"]
cover:
  image: images/cloudformation.jpg
  hiddenInList: true
---

## Bem-vindo ao Dia 10 do nosso curso de 30 dias de AWS! 

Hoje, vamos nos aprofundar no poderoso mundo do CloudFormation, o serviço de Infraestrutura como Código (IaC) da AWS. Com o CloudFormation, você pode definir sua infraestrutura AWS em um template declarativo, permitindo o provisionamento automatizado, gerenciamento e atualizações de seus recursos.

## Compreendendo os conceitos de infraestrutura como código (IaC)

Vamos nos aprofundar nos aspectos principais:

### 1. Configuração Declarativa

**O que significa:** A configuração declarativa refere-se a definir o estado desejado da sua infraestrutura sem especificar a sequência de ações necessárias para alcançar esse estado.

**Exemplo:** No IaC, você descreve a configuração da sua infraestrutura usando templates (por exemplo, templates CloudFormation na AWS) que descrevem os recursos e suas propriedades. Você declara quais recursos deseja (por exemplo, instâncias EC2, bancos de dados, balanceadores de carga) e suas configurações sem detalhar como esses recursos devem ser provisionados.

### 2. Controle de Versão e Colaboração

**O que significa:** O IaC permite que as configurações de infraestrutura sejam versionadas e gerenciadas usando sistemas de controle de versão como Git, permitindo colaboração e garantindo consistência entre ambientes.

**Exemplo:** As equipes podem colaborar em mudanças de infraestrutura criando branches, revisando alterações e mesclando-as na base de código principal. Essa abordagem garante que as mudanças na infraestrutura sejam documentadas, reversíveis e auditáveis.

### 3. Provisionamento Automatizado e Orquestração

**O que significa:** O IaC permite a automação dos processos de provisionamento, escalabilidade e gerenciamento de infraestrutura através de configuração baseada em código.

**Exemplo:** Com ferramentas IaC como CloudFormation, Terraform ou AWS CDK (Cloud Development Kit), você pode definir seus requisitos de infraestrutura em código e usar pipelines de automação para implantar e gerenciar recursos. Isso reduz a intervenção manual, acelera os ciclos de implantação e minimiza o risco de desvio de configuração.

### 4. Infraestrutura Imutável

**O que significa:** A infraestrutura imutável é um conceito onde os componentes de infraestrutura são substituídos em vez de modificados, garantindo consistência e confiabilidade.

**Exemplo:** No IaC, em vez de modificar recursos existentes, você cria novos recursos com as configurações desejadas e substitui os antigos. Essa abordagem reduz o risco de erros de configuração e torna os processos de rollback mais confiáveis.

### 5. Escalabilidade e Flexibilidade

**O que significa:** O IaC permite que a infraestrutura seja facilmente escalada para cima ou para baixo para atender a demandas em mudança, proporcionando flexibilidade e agilidade.

**Exemplo:** Definindo padrões de infraestrutura escaláveis em templates IaC, você pode automatizar o provisionamento de recursos adicionais com base nas demandas de carga de trabalho. Por exemplo, você pode escalar automaticamente instâncias EC2 ou adicionar mais réplicas de banco de dados durante períodos de tráfego intenso.

### 6. Teste e Validação de Infraestrutura

**O que significa:** O IaC facilita o teste automatizado e a validação das configurações de infraestrutura, garantindo confiabilidade e conformidade.

**Exemplo:** Você pode usar ferramentas como AWS Config, AWS Config Rules ou frameworks de teste de terceiros para validar as configurações de infraestrutura em relação a políticas e práticas recomendadas predefinidas. Isso ajuda a identificar configurações incorretas, vulnerabilidades de segurança e violações de conformidade cedo no ciclo de desenvolvimento.

## Escrevendo templates CloudFormation

Escrever templates CloudFormation para provisionar recursos AWS envolve criar documentos JSON ou YAML que definem o estado desejado da sua infraestrutura. Esses templates servem como planos para seus recursos AWS e configurações. Vamos dividir o processo:

### 1. Escolhendo os Tipos de Recursos Corretos

O CloudFormation suporta uma ampla gama de tipos de recursos AWS, incluindo instâncias EC2, buckets S3, bancos de dados RDS, roles IAM, VPCs e mais. Cada tipo de recurso tem propriedades e atributos específicos que você pode configurar para atender aos seus requisitos.

### 2. Definindo Recursos e Propriedades

No seu template CloudFormation, você define os recursos AWS que deseja criar, junto com suas propriedades. Os recursos são definidos na seção 'Resources' do template. Cada recurso deve ter um nome lógico e especificar seu tipo (por exemplo, 'AWS::EC2::Instance' para uma instância EC2). As propriedades são definidas na seção 'Properties' de cada recurso e determinam a configuração do recurso.

### 3. Referenciando Outros Recursos

O CloudFormation permite que você referencie atributos de outros recursos dentro do seu template. Isso permite criar dependências entre recursos e garantir o sequenciamento correto durante a criação e atualizações de stacks.

### 4. Usando Funções Intrínsecas

O CloudFormation fornece funções intrínsecas que permitem realizar operações dinâmicas dentro dos seus templates. Funções intrínsecas comuns incluem 'Ref', 'Fn::GetAtt', 'Fn::Sub', 'Fn::Join' e 'Fn::ImportValue'. Essas funções permitem recuperar valores, realizar substituições de strings, concatenar strings e importar valores de outras stacks ou exportações.

### 5. Lidando com Dependências e Ordem

Ao definir recursos que dependem uns dos outros, certifique-se de estabelecer as dependências necessárias usando o atributo 'DependsOn' ou funções intrínsecas. Isso garante que os recursos sejam criados ou atualizados na ordem correta para evitar problemas de dependência.

### 6. Organizando Seu Template

Mantenha seu template CloudFormation bem organizado e modular. Considere dividir templates grandes em componentes menores e reutilizáveis usando stacks aninhadas, módulos CloudFormation da AWS ou templates do AWS Serverless Application Model (SAM). Templates modulares melhoram a legibilidade, a manutenção e a reutilização.

### Exemplo de Template CloudFormation

```yaml
Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro
      ImageId: ami-0c55b159cbfafe1f0
      KeyName: my-key-pair
      SecurityGroups:
        - sg-12345678
```

Neste exemplo:

- Definimos uma instância EC2 chamada 'MyEC2Instance'.
- A instância usa o tipo 't2.micro' e a Amazon Machine Image (AMI) especificada.
- Atribuímos um par de chaves ('my-key-pair') e um grupo de segurança ('sg-12345678') à instância.

## Lançamento de stacks e atualização de recursos

Lançar stacks e atualizar recursos é um aspecto fundamental do gerenciamento de infraestrutura como código (IaC) na AWS. O CloudFormation permite que você crie, atualize e exclua coleções de recursos AWS de maneira controlada e automatizada usando templates. Vamos explorar o lançamento de stacks e a atualização de recursos com o CloudFormation:

### Lançamento de Stacks

1. **Prepare Seu Template CloudFormation:**

   Escreva um template CloudFormation (em formato JSON ou YAML) que defina os recursos AWS que você deseja provisionar.
   Certifique-se de que seu template segue a sintaxe correta e inclui todos os recursos e configurações necessários.

2. **Escolha um Método de Implantação:**

   O CloudFormation oferece vários métodos de implantação, incluindo o Console de Gerenciamento da AWS, AWS CLI, SDKs da AWS e APIs do CloudFormation.
   Escolha o método de implantação que melhor se adapta ao seu fluxo de trabalho e requisitos de automação.

3. **Especifique Parâmetros da Stack (Opcional):**

   Se seu template CloudFormation incluir parâmetros, forneça valores de entrada para esses parâmetros durante a criação da stack.
   Os parâmetros permitem personalizar o comportamento do seu template sem modificar seu conteúdo.

4. **Lance a Stack:**

   Use o método de implantação selecionado para criar uma nova stack CloudFormation com base no seu template.
   Especifique o nome da stack, o caminho do arquivo template e quaisquer parâmetros necessários.

5. **Monitore a Criação da Stack:**

   O CloudFormation fornece atualizações detalhadas de progresso e status durante a criação da stack.
   Monitore o console do CloudFormation ou a saída da linha de comando para acompanhar o progresso da criação da stack e identificar quaisquer problemas.

6. **Verifique os Recursos da Stack:**

   Após a conclusão do processo de criação da stack, verifique se os recursos provisionados correspondem às suas expectativas.
   Use o Console de Gerenciamento da AWS ou ferramentas de linha de comando para inspecionar os recursos criados pela stack.

### Atualização de Recursos

1. **Modifique Seu Template CloudFormation:**

   Atualize seu template CloudFormation para refletir as alterações desejadas nos recursos AWS.
   Faça os ajustes necessários nas configurações, propriedades ou dependências dos recursos.

2. **Escolha o Método de Atualização:**

   O CloudFormation suporta dois métodos de atualização: atualizações de stack e atualizações de recursos.
   As atualizações de stack envolvem a modificação da stack inteira, carregando um novo template ou atualizando parâmetros de template existentes.
   As atualizações de recursos permitem modificar recursos específicos dentro de uma stack

sem afetar outros recursos.

3. **Inicie a Atualização da Stack:**

   Use o console do CloudFormation, AWS CLI, SDKs ou APIs para iniciar uma atualização da stack.
   Especifique o nome da stack e forneça o template CloudFormation atualizado ou parâmetros modificados.

4. **Monitore o Progresso da Atualização:**

   Assim como na criação da stack, monitore o progresso da atualização da stack para garantir que seja concluída com sucesso.
   O CloudFormation fornece atualizações detalhadas de status e mensagens de erro para ajudar na resolução de problemas.

5. **Rollback e Limpeza (Opcional):**

   Se a atualização da stack encontrar erros ou não conseguir ser concluída, o CloudFormation inicia automaticamente um rollback para o estado anterior da stack.
   Revise os eventos de rollback e mensagens de erro para identificar problemas e tomar ações corretivas.

6. **Verifique os Recursos Atualizados:**

   Após a conclusão bem-sucedida da atualização da stack, verifique se os recursos atualizados refletem as alterações desejadas.
   Use ferramentas e serviços da AWS para validar as configurações e a funcionalidade dos recursos.

### Exemplos de código

Abaixo, fornecerei exemplos de snippets de código para lançar uma stack CloudFormation, atualizar recursos dentro da stack e um template CloudFormation simples.

#### Template CloudFormation Exemplo

Vamos criar um template CloudFormation básico ('example-template.yaml') que define um bucket S3:

```yaml
Resources:
  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: my-unique-bucket-name
```

#### Lançando uma Stack (AWS CLI)

```bash
aws cloudformation create-stack \
  --stack-name MyStack \
  --template-body file://example-template.yaml
```

#### Atualizando Recursos (AWS CLI)

Vamos supor que queremos atualizar o template CloudFormation para adicionar uma nova política de bucket S3.

Template CloudFormation Atualizado ('updated-template.yaml'):

```yaml
Resources:
  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: my-unique-bucket-name

  MyBucketPolicy:
    Type: AWS::S3::BucketPolicy
    Properties:
      Bucket: !Ref MyS3Bucket
      PolicyDocument:
        Statement:
          - Effect: Allow
            Principal: "*"
            Action: "s3:GetObject"
            Resource: !Sub "arn:aws:s3:::${MyS3Bucket}/*"
```

#### Comando de Atualização da Stack (AWS CLI)

```bash
aws cloudformation update-stack \
  --stack-name MyStack \
  --template-body file://updated-template.yaml
```

Esses comandos demonstram como criar uma stack CloudFormation e atualizar recursos dentro dela usando a AWS CLI.

Lembre-se de substituir 'MyStack', 'example-template.yaml' e 'updated-template.yaml' pelos nomes reais da sua stack e caminhos dos arquivos de template.

Você pode executar esses comandos no seu terminal ou integrá-los aos seus scripts de automação ou pipelines CI/CD para um gerenciamento de infraestrutura contínuo.

## Perguntas de entrevista baseadas em cenários

Aqui estão perguntas de entrevista baseadas em cenários e respostas focando no CloudFormation, infraestrutura como código (IaC), gerenciamento de stacks e atualização de recursos:

**Cenário: Explique o conceito de Infraestrutura como Código (IaC) e como ele beneficia a implantação e o gerenciamento de infraestrutura em nuvem.**
- **Resposta:** Infraestrutura como Código (IaC) é a prática de gerenciar e provisionar infraestrutura através de arquivos de definição legíveis por máquina, em vez de processos manuais. Aqui está como ele beneficia a infraestrutura em nuvem:

    - Consistência: O IaC garante a implantação consistente em diferentes ambientes, reduzindo o desvio de configuração.
    - Escalabilidade: Ele permite fácil escalabilidade da infraestrutura para atender a demandas em mudança.
    - Controle de Versão: O código de infraestrutura pode ser versionado e gerenciado, facilitando a colaboração e a auditoria.
    - Automação: Com o IaC, você automatiza todo o ciclo de vida da infraestrutura, reduzindo erros e acelerando a implantação.

**Cenário: Você precisa provisionar um ambiente AWS consistindo de uma instância EC2 e um bucket S3. Como você escreveria um template CloudFormation para conseguir isso?**
- **Resposta:** Eu criaria um template CloudFormation (YAML ou JSON) definindo os recursos da seguinte forma:

    - Um recurso de instância EC2 do tipo 'AWS::EC2::Instance'.
    - Um recurso de bucket S3 do tipo 'AWS::S3::Bucket'.
    - Eu especificaria propriedades como tipo de instância, ID da imagem, nome do bucket, etc., dentro do template.

**Cenário: Você escreveu um template CloudFormation e precisa implantá-lo. Explique o processo de lançamento de uma stack CloudFormation usando a AWS CLI.**
- **Resposta:** Para lançar uma stack CloudFormation usando a AWS CLI, você usa o comando `aws cloudformation create-stack`. Forneça o nome da stack e o caminho para o template CloudFormation usando o parâmetro `--template-body`. Opcionalmente, você pode especificar parâmetros de stack usando a flag `--parameters`.

**Cenário: Você fez alterações em um template CloudFormation existente e precisa atualizar a stack correspondente sem causar tempo de inatividade. Como você abordaria isso?**
- **Resposta:** Eu usaria o comando `aws cloudformation update-stack` para atualizar a stack. Eu especificaria o nome da stack e o caminho para o template CloudFormation atualizado usando o parâmetro `--template-body`. O CloudFormation executará uma atualização gradual, garantindo alta disponibilidade ao atualizar recursos de maneira controlada.

## Conclusão

O CloudFormation simplifica o gerenciamento de infraestrutura tratando seus recursos AWS como código. Hoje, arranhamos a superfície do que é possível com o CloudFormation. À medida que você explora mais, descobrirá suas amplas capacidades para orquestrar arquiteturas complexas com facilidade.

Fique atento ao tópico de amanhã, onde exploraremos outros serviços AWS. Feliz computação em nuvem!
