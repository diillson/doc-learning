---
title: "Dia 2: Console de Gerenciamento da AWS"
date: 2024-07-27
tags: ["AWS", "Cloud Computing", "Console de Gerenciamento", "IAM", "Devops", "Treinamento"]
description: "Explore o Console de Gerenciamento da AWS, dominando a navegação, o IAM e os serviços da AWS. Entenda como utilizar essas ferramentas para otimizar segurança e controle de acesso."
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia2"]
author: ["Edilson Freitas"]
cover:
   image: images/awsmanagement.jpeg
   hiddenInList: true
---

## Bem-vindo ao Dia 2 da sua jornada de 30 dias na AWS!

🚀 Hoje, vamos explorar o coração da AWS: o Console de Gerenciamento. Durante esta aventura, você ganhará insights valiosos sobre como navegar pelo console, dominar o IAM (Identity and Access Management) e explorar a vasta gama de serviços da AWS à sua disposição.

### Navegando pelo Console de Gerenciamento da AWS

Entender como se movimentar pelo console de maneira eficiente é uma habilidade fundamental para qualquer pessoa que trabalha com serviços da AWS. Aqui está um guia detalhado sobre a navegação no Console de Gerenciamento da AWS:

1. **Login no Console:**
    - Para acessar o Console de Gerenciamento da AWS, você precisa fazer login com suas credenciais da conta AWS.
    - Visite a [página do Console de Gerenciamento da AWS](https://aws.amazon.com/console/) e faça login usando seu nome de usuário e senha.

2. **Visão Geral do Dashboard:**
    - Após o login, você será direcionado ao dashboard, que fornece uma visão geral de seus recursos da AWS e atividades recentes.
    - Métricas chave, atalhos de serviços e alertas podem ser exibidos aqui, dependendo de sua configuração.

3. **Menu de Serviços:**
    - O menu de Serviços, localizado no topo do console, oferece acesso a todos os serviços da AWS.
    - Os serviços são organizados em categorias como Computação, Armazenamento, Banco de Dados, Aprendizado de Máquina, Segurança e mais.
    - Clicar em uma categoria revela um menu dropdown listando os serviços relevantes.

4. **Barra de Pesquisa:**
    - A barra de pesquisa no topo do console permite que você encontre rapidamente serviços, recursos ou recursos da AWS.
    - Você pode digitar palavras-chave ou nomes de serviços para iniciar uma busca. O console fornecerá sugestões enquanto você digita.

5. **Páginas de Serviços:**
    - Clicar em um serviço específico no menu de Serviços ou usar a barra de pesquisa leva você à página do serviço.
    - Cada página de serviço fornece acesso a vários recursos, opções de configuração e ferramentas de gerenciamento de recursos específicos daquele serviço.
    - A navegação dentro de uma página de serviço geralmente envolve abas ou um menu lateral para diferentes seções.

6. **Navegação Breadcrumb:**
    - A navegação breadcrumb está disponível no topo da interface do console e fornece um rastro das páginas que você visitou.
    - Você pode clicar em qualquer nível do breadcrumb para navegar rapidamente de volta a uma página de nível superior.

7. **Opções de Personalização:**
    - O Console de Gerenciamento da AWS permite personalização para ajustar a interface às suas preferências.
    - Você pode personalizar o layout do dashboard, adicionar ou remover widgets e organizar atalhos para serviços usados com frequência.

8. **Documentação e Ajuda:**
    - A AWS oferece documentação extensa e ajuda contextual em toda a interface do console.
    - Procure pelos links de "Documentação", ícones de "?" ou dicas de ajuda para acessar documentação e recursos relevantes.

9. **Seleção de Região:**
    - A AWS opera em várias regiões globalmente, e você pode alternar entre regiões usando o seletor de região.
    - Diferentes regiões podem oferecer diferentes serviços ou ter estruturas de preços variadas.

10. **Configurações da Conta:**
    - Acesse suas configurações de conta, informações de faturamento e credenciais de segurança através do menu dropdown da conta.
    - É essencial gerenciar suas configurações de conta e configurações de segurança para garantir a integridade e a segurança dos seus recursos da AWS.

### Entendendo o IAM (Identity and Access Management)

IAM é um componente crucial da segurança da AWS que permite controlar o acesso aos serviços e recursos da AWS de forma segura. Entender o IAM e criar usuários IAM é fundamental para gerenciar permissões e garantir o princípio do menor privilégio em seu ambiente AWS. Aqui está uma explicação abrangente:

1. **Compreendendo o IAM:**
    - O IAM permite gerenciar usuários, grupos, funções e políticas para controlar o acesso aos recursos da AWS.
    - Ele fornece controle granular sobre quem pode acessar recursos específicos e quais ações podem ser realizadas.
    - O IAM opera com base no princípio do menor privilégio, concedendo aos usuários apenas as permissões necessárias para realizar suas tarefas.

2. **Conceitos Chave do IAM:**
    - **Usuários:** Representam indivíduos ou serviços que interagem com a AWS. Cada usuário tem um conjunto único de credenciais de segurança.
    - **Grupos:** Coleções de usuários com permissões similares. Você atribui permissões a grupos em vez de a usuários individuais para facilitar o gerenciamento.
    - **Funções:** As funções do IAM são semelhantes aos usuários, mas são destinadas a recursos da AWS em vez de indivíduos. Elas definem um conjunto de permissões para qualquer pessoa ou coisa que assuma aquela função.
    - **Políticas:** Documentos JSON que definem permissões. Você anexa políticas a usuários, grupos ou funções para conceder acesso a recursos e ações específicos.

3. **Criando Usuários IAM:**
    - Para criar um usuário IAM, você precisa fazer login no Console de Gerenciamento da AWS usando sua conta root ou um usuário IAM com permissões administrativas.
    - Navegue até o dashboard do IAM e selecione "Usuários" no menu lateral.
    - Clique no botão "Adicionar usuário" e forneça um nome de usuário para o novo usuário.
    - Escolha o tipo de acesso para o usuário: Acesso programático (para acessar a AWS programaticamente usando APIs) e/ou acesso ao Console de Gerenciamento da AWS.
    - Defina permissões para o usuário adicionando-o a um ou mais grupos IAM ou anexando políticas diretamente ao usuário.
    - Revise os detalhes do usuário e complete o processo de criação do usuário.

4. **Melhores Práticas para o IAM:**
    - **Use Funções IAM:** Em vez de compartilhar chaves de acesso, use funções IAM para aplicações e serviços executados em instâncias EC2, funções Lambda ou outros recursos da AWS.
    - **Implemente Autenticação Multifator (MFA):** Habilite a MFA para usuários IAM para adicionar uma camada extra de segurança.
    - **Revise Regularmente as Permissões:** Revise e audite periodicamente as políticas IAM e permissões de usuários para garantir que estejam alinhadas com seus requisitos de segurança.
    - **Siga o Princípio do Menor Privilégio:** Conceda aos usuários apenas as permissões necessárias para realizar suas tarefas e evite conceder permissões excessivamente amplas.

5. **Exemplo: Concedendo Permissões de Acesso:**
    - Suponha que você queira conceder a um usuário IAM chamado “Edilson” permissão para gerenciar instâncias EC2. Você pode criar uma política IAM personalizada com as permissões necessárias:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "ec2:*",
      "Resource": "*"
    }
  ]
}
```

 - Esta política permite que o usuário "Edilson" execute todas as ações ('ec2:*') em todos os recursos EC2 (*).

## Explorando os Serviços da AWS

Explorar os diferentes serviços da AWS disponíveis no console é uma jornada empolgante que revela uma vasta gama de ferramentas e recursos adaptados a vários casos de uso. Aqui está uma visão geral de como você pode explorar e entender a multiplicidade de serviços da AWS disponíveis:

### Navegando pelo Menu de Serviços da AWS

O Console de Gerenciamento da AWS oferece acesso a uma ampla gama de serviços categorizados em vários domínios como Computação, Armazenamento, Banco de Dados, Redes, Aprendizado de Máquina, Análise, Segurança e mais. Comece navegando pelo menu de Serviços localizado no topo do console. Clicar no menu revela uma lista dropdown de categorias de serviços e serviços individuais.

### Entendendo as Categorias de Serviços

- **Computação:** Explore serviços como Amazon EC2 para servidores virtuais, AWS Lambda para computação sem servidor e Amazon ECS para gerenciamento de contêineres.
- **Armazenamento:** Descubra soluções de armazenamento como Amazon S3 para armazenamento de objetos, Amazon EBS para armazenamento em bloco e Amazon Glacier para armazenamento arquivístico.
- **Banco de Dados:** Conheça serviços de banco de dados gerenciados como Amazon RDS para bancos de dados relacionais, Amazon DynamoDB para bancos de dados NoSQL e Amazon Redshift para data warehousing.
- **Redes:** Explore serviços de rede incluindo Amazon VPC para nuvens privadas virtuais, Amazon Route 53 para gerenciamento de sistema de nomes de domínio (DNS) e AWS Direct Connect para conexões de rede dedicadas.
- **Aprendizado de Máquina:** Mergulhe em serviços de aprendizado de máquina como Amazon SageMaker para construção, treinamento e implantação de modelos de ML, e Amazon Comprehend para processamento de linguagem natural.
- **Análise:** Descubra serviços de análise como Amazon Athena para consultas de dados no S3 usando SQL, Amazon EMR para processamento de big data e Amazon Kinesis para streaming de dados em tempo real.
- **Segurança e Identidade:** Aprenda sobre serviços de segurança como AWS Identity and Access Management (IAM) para controle de acesso, Amazon GuardDuty para detecção de ameaças e AWS Key Management Service (KMS) para gerenciamento de chaves de criptografia.

### Explorando Serviços Individuais

Selecione um serviço no menu para explorar seus recursos, funcionalidades e detalhes de preços. Cada serviço possui seu próprio dashboard ou console de gerenciamento onde você pode configurar definições, gerenciar recursos e acessar documentação. Aproveite tutoriais, guias de início rápido e casos de uso fornecidos pela AWS para ganhar experiência prática com os serviços.

### Experimentando com Serviços do Free Tier

A AWS oferece um Free Tier que permite aos usuários explorar e experimentar muitos serviços sem custo por um período limitado. Aproveite os serviços elegíveis do Free Tier para ganhar experiência prática sem incorrer em cobranças.

### Caminhos de Aprendizado e Documentação

Explore a documentação da AWS, whitepapers e recursos online para aprofundar seu entendimento sobre diferentes serviços. A AWS também oferece caminhos de aprendizado, cursos de treinamento e programas de certificação para ajudá-lo a se tornar proficiente no uso dos serviços da AWS.

### Comunidade e Fóruns

Participe da comunidade AWS através de fóruns, grupos de usuários e comunidades online para trocar conhecimento, fazer perguntas e compartilhar melhores práticas.

### Experimentação e Inovação

Adote uma cultura de experimentação e inovação tentando novos serviços, explorando integrações e experimentando configurações avançadas.

## Conclusão

Parabéns por navegar pelo Dia 2 do curso AWS! Ao dominar o Console de Gerenciamento da AWS e o IAM, você estabeleceu uma base sólida para sua jornada na nuvem. À medida que continua sua exploração, lembre-se de aproveitar a interface intuitiva do console e o poder do IAM para otimizar a segurança e o controle de acesso.

Fique ligado para a aventura de amanhã, onde vamos nos aprofundar no rico ecossistema de serviços da AWS. Feliz computação em nuvem! ☁️💻

