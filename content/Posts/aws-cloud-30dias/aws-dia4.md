---
title: "Dia 4: S3 (Simple Storage Service)"
date: 2024-08-01
tags: ["AWS", "Cloud Computing", "S3", "Armazenamento", "Lifecycle Policies", "DevOps", "Treinamento"]
description: "Explore o S3 da AWS, entenda seus casos de uso, como criar buckets, gerenciar objetos, implementar versionamento e políticas de ciclo de vida."
series: ["aws em 30 dias"]
weight: 1
aliases: ["/aws-dia4"]
author: ["Edilson Freitas"]
cover:
  image: images/s3.png
  hiddenInList: true
---

## Bem-vindo ao Dia 4 do nosso curso de 30 dias sobre AWS!

Hoje, vamos mergulhar em um dos serviços fundamentais fornecidos pela Amazon Web Services (AWS): o Simple Storage Service, comumente conhecido como S3. O S3 é um serviço de armazenamento de objetos altamente escalável, seguro e durável oferecido pela AWS. Na lição de hoje, exploraremos todos os aspectos do S3, incluindo seus casos de uso, como criar buckets, gerenciar objetos dentro deles e implementar recursos importantes como versionamento e políticas de ciclo de vida.

### Visão Geral do S3 e Seus Casos de Uso

O Amazon S3 (Simple Storage Service) é um serviço de armazenamento de objetos altamente escalável, durável e seguro oferecido pela AWS. Ele é projetado para armazenar e recuperar qualquer quantidade de dados de qualquer lugar na web. Aqui estão algumas características chave do Amazon S3:

- **Escalabilidade:** O S3 é construído para escalar. Ele pode lidar com quantidades virtualmente ilimitadas de dados, tornando-o adequado para aplicações de qualquer tamanho, desde pequenas startups até grandes empresas.
- **Durabilidade e Confiabilidade:** O Amazon S3 é projetado para 99.999999999% (11 noves) de durabilidade, o que significa que é altamente confiável para armazenar dados críticos. O S3 armazena dados de forma redundante em várias instalações e dispositivos dentro de uma região da AWS.
- **Segurança:** O S3 fornece vários recursos de segurança para proteger seus dados, incluindo criptografia, listas de controle de acesso (ACLs) e políticas de bucket. Você pode controlar o acesso aos seus recursos S3 tanto no nível do bucket quanto no nível do objeto.
- **Custo-Efetivo:** Com seu modelo de preços pay-as-you-go, o S3 oferece soluções de armazenamento custo-efetivas para uma ampla gama de casos de uso. Você paga apenas pelo armazenamento que usa, sem custos iniciais ou compromissos de longo prazo.

### Casos de Uso do Amazon S3

1. **Hospedagem de Websites Estáticos:**
   - O Amazon S3 pode hospedar websites estáticos ao servir arquivos HTML, CSS, JavaScript e outros arquivos estáticos diretamente dos buckets S3. Isso o torna uma solução ideal para hospedar websites de baixo tráfego, páginas de destino ou sites de documentação.

2. **Backup e Arquivamento de Dados:**
   - Muitas organizações usam o Amazon S3 como uma solução segura e durável para fazer backup e arquivar seus dados. A confiabilidade e escalabilidade do S3 o tornam bem adequado para armazenamento de dados a longo prazo.

3. **Armazenamento e Distribuição de Mídia:**
   - O S3 é comumente usado para armazenar e distribuir arquivos de mídia como imagens, vídeos e arquivos de áudio. Redes de entrega de conteúdo (CDNs) podem ser integradas com o S3 para entregar conteúdo de mídia aos usuários ao redor do mundo com baixa latência.

4. **Lagos de Dados:**
   - O S3 serve como um componente fundamental para a construção de lagos de dados, que são repositórios centralizados que armazenam dados estruturados e não estruturados em qualquer escala. Lagos de dados permitem que as organizações realizem análises, aprendizado de máquina e outras tarefas de processamento de dados em grandes quantidades de dados.

5. **Armazenamento de Dados de Aplicações:**
   - O Amazon S3 é frequentemente usado como backend de armazenamento para aplicações, proporcionando uma solução confiável e escalável para armazenar conteúdo gerado pelo usuário, logs de aplicações, backups e outros dados de aplicações.

6. **Análise de Big Data:**
   - O S3 integra-se perfeitamente com vários serviços de análise da AWS, como Amazon Athena, Amazon Redshift e Amazon EMR, permitindo que as organizações analisem grandes conjuntos de dados armazenados no S3 usando consultas SQL, data warehousing ou frameworks de processamento de big data.

7. **Entrega de Conteúdo:**
   - O S3 trabalha em conjunto com o AWS CloudFront, uma rede de entrega de conteúdo (CDN), para entregar conteúdo aos usuários com baixa latência e altas velocidades de transferência. Isso é particularmente útil para servir ativos estáticos, como imagens, vídeos e documentos, a um público global.

### Criando Buckets S3 e Gerenciando Objetos

É essencial entender como criar buckets S3 e gerenciar objetos dentro deles de maneira eficaz.

#### Criando um Bucket S3

1. **Acesse o Console de Gerenciamento da AWS:**
   - Faça login no seu Console de Gerenciamento da AWS.

2. **Navegue até o S3:**
   - No menu de serviços, selecione S3 em "Storage".

3. **Clique em “Create bucket”:**
   - Esta ação inicia o processo de criação de um novo bucket.

4. **Configure as Propriedades do Bucket:**
   - **Nome do Bucket:** Insira um nome de bucket globalmente único. O nome do bucket deve seguir as convenções de nomenclatura DNS e não deve conter letras maiúsculas ou sublinhados.
   - **Região:** Escolha a região da AWS onde você deseja criar seu bucket. Considere selecionar uma região mais próxima dos seus usuários para minimizar a latência.
   - **Configurar Opções:** Você pode configurar opções adicionais como versionamento, logging e tags conforme suas necessidades.

5. **Defina as Permissões do Bucket:**
   - Defina as configurações de controle de acesso para seu bucket. Você pode especificar quem pode acessar seu bucket e quais ações podem realizar.
   - Use políticas de bucket e Listas de Controle de Acesso (ACLs) para gerenciar permissões.

6. **Revisar e Criar:**
   - Revise suas configurações para garantir que estejam alinhadas com seus requisitos. Uma vez satisfeito, clique no botão “Create bucket” para criar seu bucket S3.

#### Gerenciando Objetos dentro dos Buckets S3

Uma vez que seu bucket S3 é criado, você pode começar a gerenciar objetos dentro dele. Objetos no S3 podem ser qualquer coisa, desde documentos e imagens até vídeos e dados de aplicações.

1. **Carregar Objetos:**
   - Use o Console de Gerenciamento da AWS, AWS CLI ou SDKs para carregar objetos no seu bucket S3.
   - Navegue até seu bucket dentro do Console de Gerenciamento da AWS e clique no botão “Upload” para selecionar arquivos do seu computador local.

2. **Baixar Objetos:**
   - Da mesma forma, você pode baixar objetos do seu bucket S3 usando vários métodos, incluindo o Console de Gerenciamento da AWS e CLI.
   - Selecione o objeto que deseja baixar e escolha a ação apropriada.

3. **Gerenciar Propriedades do Objeto:**
   - O S3 permite que você defina metadados e propriedades para cada objeto. Metadados podem incluir informações como tipo de conteúdo, controle de cache e tags personalizadas.
   - Você pode modificar as propriedades do objeto usando o Console de Gerenciamento da AWS ou programaticamente através dos SDKs da AWS.

4. **Versionamento:**
   - Habilite o versionamento para seu bucket S3 para manter múltiplas versões de um objeto. Este recurso ajuda a rastrear alterações e recuperar de deleções ou modificações acidentais.
   - O versionamento pode ser gerenciado através do Console de Gerenciamento da AWS ou via chamadas de API.

5. **Excluindo Objetos:**
   - Quando os objetos não são mais necessários, você pode excluí-los do seu bucket S3.
   - Use o Console de Gerenciamento da AWS, AWS CLI ou SDKs para excluir objetos individualmente ou em massa.

### Implementando Versionamento e Políticas de Ciclo de Vida

Estas funcionalidades aprimoram o gerenciamento e a durabilidade dos seus objetos, além de otimizar os custos de armazenamento. Vamos nos aprofundar em cada um desses recursos:

#### Versionamento

O versionamento no Amazon S3 permite que você mantenha múltiplas variantes de um objeto no mesmo bucket. Habilitar o versionamento é crucial para manter a integridade dos dados e mitigar o risco de deleções ou sobrescritas acidentais.

**Como Habilitar o Versionamento:**

1. **Usando o Console de Gerenciamento da AWS:**
   - Navegue até o seu bucket S3 no Console de Gerenciamento da AWS.
   - Selecione o bucket e clique na aba “Properties”.
   - Role para baixo até encontrar a seção “Versioning” e clique em “Enable versioning”.

2. **Usando o AWS CLI:**
   - Execute o seguinte comando AWS CLI para habilitar o versionamento para um bucket:

```sh
aws s3api put-bucket-versioning --bucket seu-nome-do-bucket --versioning-configuration Status=Enabled
```

**Benefícios Chave do Versionamento:**

- **Proteção contra Deleção Acidental:** Mesmo que um objeto seja deletado, suas versões anteriores permanecem acessíveis, reduzindo o risco de perda de dados.
- **Recuperação de Dados:** Recupere e restaure versões anteriores

de objetos conforme necessário, proporcionando uma rede de segurança contra alterações inadvertidas.
- **Trilhas de Auditoria:** O versionamento permite rastrear mudanças ao longo do tempo, facilitando os requisitos de conformidade e auditoria.

#### Políticas de Ciclo de Vida

As políticas de ciclo de vida no Amazon S3 automatizam o gerenciamento de objetos com base em regras predefinidas. Estas regras definem ações como transição de objetos para diferentes classes de armazenamento ou exclusão permanente após uma duração especificada.

**Como Implementar Políticas de Ciclo de Vida:**

1. **Usando o Console de Gerenciamento da AWS:**
    - Navegue até o seu bucket S3 no Console de Gerenciamento da AWS.
    - Selecione o bucket e clique na aba “Management”.
    - Em “Lifecycle rules”, clique em “Add lifecycle rule” para definir sua política.

2. **Usando o AWS CLI:**
    - Crie um arquivo JSON especificando sua configuração de ciclo de vida e aplique-o ao seu bucket usando o AWS CLI:

```sh
aws s3api put-bucket-lifecycle-configuration --bucket seu-nome-do-bucket --lifecycle-configuration file://lifecycle-config.json
```

**Exemplos de Políticas de Ciclo de Vida:**

- **Transição para Glacier:** Mova automaticamente objetos para o Amazon Glacier, uma classe de armazenamento de menor custo otimizada para arquivamento de dados, após um certo período.
- **Expiração:** Defina regras para excluir objetos após atingirem uma idade especificada, ajudando a gerenciar os custos de armazenamento e cumprir com as políticas de retenção de dados.
- **Ações Personalizadas:** Implemente ações de ciclo de vida personalizadas, como invocar funções AWS Lambda para executar tarefas específicas em objetos com base em critérios definidos.

### Exemplos de Código para Trabalhar com Versionamento, Políticas de Ciclo de Vida e Gerenciamento de Objetos no S3

#### Habilitando o Versionamento

Usando AWS CLI:

```sh
aws s3api put-bucket-versioning --bucket seu-nome-do-bucket --versioning-configuration Status=Enabled
```

#### Configurando uma Política de Ciclo de Vida

Exemplo de Política de Ciclo de Vida em JSON:

```json
{
  "Rules": [
    {
      "ID": "MoveToGlacier",
      "Status": "Enabled",
      "Prefix": "",
      "Transitions": [
        {
          "Days": 30,
          "StorageClass": "GLACIER"
        }
      ],
      "Expiration": {
        "Days": 365
      }
    }
  ]
}
```

Aplicando a Política de Ciclo de Vida Usando AWS CLI:

```sh
aws s3api put-bucket-lifecycle-configuration --bucket seu-nome-do-bucket --lifecycle-configuration file://lifecycle-policy.json
```

#### Carregando Objetos no Bucket S3

Usando AWS CLI:

```sh
aws s3 cp seu-arquivo.txt s3://seu-nome-do-bucket/
```

Usando AWS SDK para Python (Boto3):

```python
import boto3

# Cria um cliente S3
s3 = boto3.client('s3')

# Carrega o arquivo para o bucket S3
s3.upload_file('seu-arquivo.txt', 'seu-nome-do-bucket', 'seu-arquivo.txt')
```

#### Gerenciando Objetos no Bucket S3

Listando Objetos em um Bucket Usando AWS CLI:

```sh
aws s3 ls s3://seu-nome-do-bucket/
```

Excluindo Objetos Usando AWS CLI:

```sh
aws s3 rm s3://seu-nome-do-bucket/seu-arquivo.txt
```

Excluindo Objetos Usando Boto3 (Python SDK):

```python
import boto3

# Cria um cliente S3
s3 = boto3.client('s3')

# Exclui o objeto do bucket S3
s3.delete_object(Bucket='seu-nome-do-bucket', Key='seu-arquivo.txt')
```

### Questões de Entrevista Baseadas em Cenários para Engenheiros DevOps com Foco no Amazon S3

#### Cenário: Sua equipe acidentalmente sobrescreveu um arquivo importante em um bucket S3. Como você recuperaria a versão anterior do arquivo?
**Resposta:** Eu verificaria primeiro se o versionamento está habilitado no bucket S3. Se o versionamento estiver habilitado, usaria o Console de Gerenciamento da AWS ou o AWS CLI para listar todas as versões do arquivo e recuperar a versão desejada. Se o versionamento não estiver habilitado, infelizmente, não haveria versões anteriores para recuperar.

#### Cenário: Sua organização quer reduzir os custos de armazenamento movendo arquivos raramente acessados para o Amazon Glacier após 90 dias e excluindo arquivos mais antigos que um ano. Como você implementaria isso usando políticas de ciclo de vida do S3?
**Resposta:** Eu definiria uma política de ciclo de vida no formato JSON especificando a regra de transição para mover objetos para o Glacier após 90 dias e uma regra de expiração para excluir objetos após um ano. Em seguida, aplicaria esta política ao bucket S3 usando o AWS CLI ou o Console de Gerenciamento.

#### Cenário: Você tem milhares de arquivos de log em um bucket S3 e precisa excluir todos os arquivos de log mais antigos que 30 dias. Como você automatizaria esse processo?
**Resposta:** Eu criaria uma política de ciclo de vida com uma regra de expiração para excluir objetos mais antigos que 30 dias. Em seguida, aplicaria esta política ao bucket S3. Alternativamente, poderia escrever um script usando o AWS SDK ou AWS CLI para listar objetos no bucket, filtrar objetos com base na data de modificação e excluir os objetos elegíveis programaticamente.

#### Cenário: Sua equipe precisa carregar arquivos grandes em um bucket S3 de forma segura e eficiente. Como você realizaria essa tarefa?
**Resposta:** Eu recomendaria o uso do AWS CLI ou SDKs, pois eles suportam uploads multi-part para arquivos grandes. Este recurso divide o arquivo em partes menores e as carrega simultaneamente, melhorando a velocidade e a confiabilidade do upload. Além disso, garantiria que o bucket S3 esteja configurado com controles de acesso apropriados para proteger os arquivos carregados.

#### Cenário: Sua organização exige conformidade estrita com as políticas de retenção de dados. Como você garantiria a conformidade ao usar o Amazon S3?
**Resposta:** Eu utilizaria o versionamento do S3 e as políticas de ciclo de vida para impor as políticas de retenção de dados. Habilitando o versionamento, podemos preservar todas as versões dos objetos, prevenindo deleções ou modificações acidentais. Além disso, configuraria políticas de ciclo de vida para transicionar objetos para a classe de armazenamento apropriada ou excluí-los com base em períodos de retenção predefinidos.

#### Cenário: Sua equipe está experimentando altos custos de armazenamento com o Amazon S3. Como você otimizaria os custos de armazenamento enquanto mantém o desempenho e a durabilidade?
**Resposta:** Eu avaliaria os padrões de uso do armazenamento e identificaria oportunidades para otimizar os custos. Isso poderia incluir a implementação de políticas de ciclo de vida para transicionar dados raramente acessados para camadas de armazenamento de menor custo, como Amazon S3 Glacier ou Glacier Deep Archive. Além disso, avaliaria os recursos de análise de classe de armazenamento e tagging de objetos para identificar e gerenciar dados que podem ser arquivados ou excluídos para reduzir os custos de armazenamento.

### Conclusão

Nesta lição, cobrimos os conceitos básicos do Amazon S3, incluindo seus casos de uso, como criar buckets, gerenciar objetos e implementar versionamento e políticas de ciclo de vida. O S3 é uma solução de armazenamento versátil e confiável que forma a espinha dorsal de muitas aplicações e serviços da AWS.

Fique atento para a lição de amanhã, onde exploraremos outro serviço essencial da AWS!
