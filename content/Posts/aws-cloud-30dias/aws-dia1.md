---
title: "Dia 1: Introdução à AWS"
date: 2024-07-28
tags: ["AWS", "Cloud Computing", "Introdução", "aws30dias", "cloud", "DevOps", "Treinamento"]
description: "Inicie sua jornada de 30 dias na AWS, entendendo a importância da AWS na computação em nuvem, conhecendo seus principais serviços e inscrevendo-se no AWS Free Tier."
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia1"]
author: ["Edilson Freitas"]
cover:
  image: images/int.jpeg
  hiddenInList: true
---

## Bem-vindo ao Dia 1 da nossa jornada de 30 dias na AWS!

🚀 Hoje, vamos mergulhar nas bases da Amazon Web Services (AWS), explorando sua importância no mundo da computação em nuvem, conhecendo a vasta gama de serviços oferecidos e iniciando sua jornada com a criação de uma conta no AWS Free Tier.

### Visão Geral dos Serviços da AWS e Sua Importância na Computação em Nuvem

É fundamental entender o imenso impacto e a utilidade da AWS no cenário tecnológico moderno.

#### Visão Geral dos Serviços da AWS

A AWS oferece um conjunto abrangente de serviços de computação em nuvem, abrangendo várias categorias como computação, armazenamento, bancos de dados, redes, aprendizado de máquina, análise, segurança e muito mais. Esses serviços são projetados para capacitar empresas e desenvolvedores a construir, implantar e gerenciar aplicações e infraestruturas com facilidade, escalabilidade e eficiência de custos.

#### Principais Categorias de Serviços da AWS

**1. Serviços de Computação:**
- **Amazon EC2 (Elastic Compute Cloud):** Oferece capacidade de computação redimensionável na nuvem, permitindo que os usuários implantem servidores virtuais para executar aplicações.
- **AWS Lambda:** Permite a computação sem servidor, permitindo executar código sem provisionar ou gerenciar servidores.

**2. Serviços de Armazenamento:**
- **Amazon S3 (Simple Storage Service):** Oferece armazenamento de objetos escalável para armazenar e recuperar dados.
- **Amazon EBS (Elastic Block Store):** Fornece volumes de armazenamento em bloco para instâncias EC2.

**3. Serviços de Banco de Dados:**
- **Amazon RDS (Relational Database Service):** Simplifica a configuração, operação e escalabilidade de bancos de dados relacionais.
- **Amazon DynamoDB:** Um serviço de banco de dados NoSQL totalmente gerenciado, projetado para alto desempenho em qualquer escala.

**4. Serviços de Rede:**
- **Amazon VPC (Virtual Private Cloud):** Fornece uma seção logicamente isolada da Nuvem AWS onde você pode lançar recursos da AWS.
- **Amazon Route 53:** Um serviço de sistema de nomes de domínio (DNS) escalável projetado para rotear usuários finais para aplicações na internet.

**5. Serviços de Aprendizado de Máquina e IA:**
- **Amazon SageMaker:** Um serviço totalmente gerenciado que permite a desenvolvedores e cientistas de dados construir, treinar e implantar modelos de aprendizado de máquina.
- **Amazon Rekognition:** Oferece análise de imagem e vídeo baseada em aprendizado profundo.

**6. Serviços de Análise:**
- **Amazon Redshift:** Um serviço de data warehouse totalmente gerenciado, projetado para análise de dados em grande escala.
- **Amazon Athena:** Permite analisar dados diretamente no Amazon S3 usando SQL padrão.

### Importância na Computação em Nuvem

- **Escalabilidade:** A AWS permite que as empresas escalem seus recursos de acordo com a demanda, garantindo desempenho ideal sem superprovisionamento ou subutilização.
- **Flexibilidade e Agilidade:** Com a AWS, as organizações podem implantar rapidamente novas aplicações e serviços, iterar rapidamente e responder às mudanças do mercado com agilidade.
- **Custo-Eficiência:** A AWS segue um modelo de preços pay-as-you-go, onde os usuários pagam apenas pelos recursos que consomem, eliminando a necessidade de investimentos iniciais em hardware e reduzindo os custos operacionais.
- **Confiabilidade e Disponibilidade:** A AWS oferece uma infraestrutura altamente confiável com múltiplos data centers e zonas de disponibilidade em todo o mundo, garantindo continuidade dos negócios e recuperação de desastres.
- **Segurança:** A AWS fornece medidas robustas de segurança para proteger dados e aplicações, incluindo criptografia, gerenciamento de identidade e acesso (IAM) e recursos de segurança de rede.
- **Inovação:** A AWS está constantemente inovando e introduzindo novos serviços e recursos, permitindo que as empresas aproveitem tecnologias de ponta, como inteligência artificial, aprendizado de máquina e Internet das Coisas (IoT) sem grandes investimentos em infraestrutura ou expertise.

### Compreendendo a Infraestrutura Global da AWS e Regiões

Entender a infraestrutura global da AWS é essencial para projetar arquiteturas de nuvem resilientes, de alto desempenho e geograficamente distribuídas.

#### Infraestrutura Global da AWS

A AWS opera uma vasta infraestrutura global composta por data centers, infraestrutura de rede e locais de borda estrategicamente distribuídos pelo mundo. Esta infraestrutura forma a espinha dorsal dos serviços da AWS e permite que os clientes implantem suas aplicações e dados mais próximos dos usuários finais para melhorar o desempenho e a confiabilidade.

**Componentes Principais da Infraestrutura Global da AWS:**
- **Regiões:** A AWS divide sua infraestrutura global em regiões geográficas. Cada região é uma área geográfica separada que consiste em várias zonas de disponibilidade. As regiões são projetadas para serem completamente isoladas umas das outras para garantir tolerância a falhas e conformidade com a residência de dados.
- **Zonas de Disponibilidade (AZs):** Dentro de cada região, a AWS constrói várias zonas de disponibilidade. Uma zona de disponibilidade é essencialmente um data center ou um cluster de data centers equipados com infraestrutura independente de energia, refrigeração e rede. As zonas de disponibilidade são isoladas umas das outras para garantir alta disponibilidade e tolerância a falhas.
- **Locais de Borda:** A AWS opera uma rede global de locais de borda que servem como pontos de extremidade para seu serviço de Content Delivery Network (CDN), o Amazon CloudFront. Os locais de borda são distribuídos nas principais cidades do mundo e são usados para armazenar em cache conteúdo mais próximo dos usuários finais, reduzindo a latência e melhorando o desempenho da entrega de conteúdo.

**Significado da Infraestrutura Global da AWS:**
- **Alta Disponibilidade:** Aproveitando múltiplas zonas de disponibilidade dentro de cada região, a AWS garante alta disponibilidade para aplicações e serviços.
- **Tolerância a Falhas:** A natureza distribuída da infraestrutura da AWS, combinada com mecanismos de redundância e isolamento, aumenta a tolerância a falhas e a resiliência.
- **Baixa Latência:** Implantando recursos em regiões e zonas de disponibilidade geograficamente distribuídas, os clientes podem minimizar a latência e melhorar a responsividade de suas aplicações.
- **Conformidade e Residência de Dados:** As regiões da AWS permitem que os clientes armazenem e processem dados em conformidade com requisitos regulatórios e leis de residência de dados.
- **Recuperação de Desastres:** A infraestrutura global da AWS serve como base para soluções robustas de recuperação de desastres. Ao replicar dados e recursos em várias regiões, os clientes podem implementar estratégias de recuperação de desastres que garantam a continuidade dos negócios em caso de desastres naturais, interrupções ou outros eventos catastróficos.

### Inscreva-se para uma Conta no AWS Free Tier

Esta é uma excelente maneira de explorar a vasta gama de serviços da AWS sem incorrer em custos iniciais. Aqui está um guia detalhado sobre como se inscrever para o AWS Free Tier:

#### Passos para Inscrever-se no AWS Free Tier:

1. **Visite a Página de Inscrição do AWS Free Tier:** Navegue até a página do [AWS Free Tier](https://aws.amazon.com/free/).
2. **Clique em “Create an AWS Account” (Criar uma Conta AWS):** Na página do AWS Free Tier, você encontrará um botão ou link destacado rotulado como “Create an AWS Account”. Clique nele para iniciar o processo de inscrição.
3. **Forneça Informações da Conta:** Você será solicitado a inserir informações básicas da conta, incluindo seu endereço de e-mail, senha e nome da conta AWS. Certifique-se de usar um endereço de e-mail válido, pois a AWS enviará notificações importantes relacionadas à conta para este e-mail.
4. **Insira Informações de Contato:** Em seguida, você precisará fornecer suas informações de contato, incluindo seu nome completo, nome da empresa (se aplicável) e número de telefone. A AWS pode usar essas informações para fins de verificação da conta.
5. **Informações de Pagamento:** A AWS exige que você forneça um método de pagamento válido, como um cartão de crédito ou débito, durante o processo de inscrição. Isso é principalmente para fins de verificação de identidade e para prevenir abuso da oferta do Free Tier. No entanto, você não será cobrado a menos que exceda os limites de uso do Free Tier ou faça upgrade para um plano pago.
6. **Verificação de Identidade:** A AWS pode exigir etapas adicionais de verificação de identidade para confirmar sua identidade e método de pagamento. Isso pode envolver uma ligação telefônica ou código de verificação SMS enviado para o número de telefone fornecido.
7. **Aceite os Termos e Condições:** Revise o [Contrato do Cliente da AWS](https://aws.amazon.com/agreement/), que descreve os termos e condições de uso dos serviços da AWS. Depois de ler e entender o contrato, marque a caixa para indicar sua aceitação.
8. **Complete a Inscrição:** Após fornecer todas as informações necessárias e concordar com os termos e condições,

 clique no botão “Create Account and Continue” (Criar Conta e Continuar) para concluir o processo de inscrição.
9. **E-mail de Confirmação:** A AWS enviará um e-mail de confirmação para o endereço fornecido durante a inscrição. Siga as instruções no e-mail para verificar seu endereço de e-mail e ativar sua conta AWS.
10. **Acesse o Console de Gerenciamento da AWS:** Uma vez que sua conta seja criada e verificada com sucesso, você pode acessar o [Console de Gerenciamento da AWS](https://aws.amazon.com/console/) usando seu endereço de e-mail e senha. O Console de Gerenciamento da AWS é a interface web onde você pode gerenciar e acessar todos os serviços e recursos da AWS.

### Explorando o AWS Free Tier

Depois de se inscrever no AWS Free Tier, você terá acesso a uma ampla gama de serviços AWS, incluindo computação, armazenamento, bancos de dados, redes e muito mais, sem custo por 12 meses. Os limites de uso do Free Tier variam para cada serviço, e a AWS fornece documentação detalhada para ajudar você a entender os limites de uso e preços.

### Conclusão

Parabéns por dar o primeiro passo rumo ao domínio da AWS! Hoje, estabelecemos as bases entendendo os conceitos principais da AWS, explorando sua infraestrutura global e iniciando sua jornada com o AWS Free Tier. Fique ligado para a aventura de amanhã, onde vamos nos aprofundar nos serviços da AWS e em implementações práticas.

### Junte-se a nós amanhã para o Dia 2: Explorando o Console de Gerenciamento da AWS! Até lá, feliz computação em nuvem! ☁️💻