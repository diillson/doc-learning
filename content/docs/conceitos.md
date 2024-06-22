---
title: "Conceitos"
description: "Conceitos importantes na utilização da plataforma de aprendizado"
icon: "article"
date: "2023-05-22T00:27:57+01:00"
lastmod: "2023-05-22T00:27:57+01:00"
draft: false
toc: true
weight: 500
---

# Identificador Único de Recursos

Em nossa plataforma de aprendizado, cada recurso, como tutoriais, cursos e artigos, possui um identificador único, garantindo que todos os conteúdos sejam referenciados de forma única e precisa.

Para integrar-se com outros sistemas ou plataformas de aprendizado, recomendamos utilizar esses identificadores para manter a consistência e integridade dos dados.

# Contabilização de Acessos

{{< alert context="info" text="Para garantir o melhor desempenho, recomendamos o uso de contas de integração para acessar os recursos da plataforma." />}}

A contabilização de acessos e interações com os recursos da plataforma é feita de forma automatizada, utilizando logs e métricas para monitorar e analisar a utilização dos conteúdos.

Para utilizar esse recurso, é necessário configurar corretamente os logs e métricas em suas aplicações, garantindo que todos os acessos sejam registrados de forma precisa.

#### Homologação de Acessos Automatizada:

A homologação de acessos consiste no processo de validação e registro de todas as interações dos usuários com os recursos da plataforma. Esse processo é essencial para garantir a integridade e a consistência dos dados de uso.

Esse processo está automatizado, eliminando a necessidade de intervenções manuais para validar e registrar os acessos.

###### Como funciona:

1. O sistema usuário solicita o acesso desejado através da interface da plataforma.
2. Caso o acesso seja autorizado, a plataforma registra a interação de forma automatizada.
3. A pessoa responsável pelo monitoramento deve acompanhar as métricas e logs para validar se os acessos foram processados corretamente.
4. Os logs de acesso são gerados e armazenados automaticamente em um diretório dedicado.
5. Em caso de inconsistências, a pessoa responsável deve entrar em contato com o suporte, informando o ID do recurso para que seja verificado.

###### Informações importantes:

{{< alert context="info" text="Não será possível a homologação de acessos retroativos. Apenas os acessos efetuados no dia corrente serão processados." />}}

#### Estrutura dos Logs de Acesso:

- **Identificador do Recurso:** UUID único para cada recurso.
- **Timestamp:** Data e hora do acesso.
- **Usuário:** Identificador do usuário que realizou o acesso.
- **Ação:** Tipo de ação realizada (visualização, download, etc.).

#### Critérios de Acesso:

- **Acesso a Tutoriais:** Registra o acesso a tutoriais específicos.
- **Acesso a Cursos:** Registra a participação em cursos e módulos.
- **Acesso a Artigos:** Registra a leitura de artigos e publicações.

# Fraudes

A plataforma de aprendizado **não** realiza análise de fraudes diretamente. O processo de análise de fraudes deve ser implementado pela equipe de segurança da sua organização, garantindo que todos os acessos e interações sejam monitorados de forma segura.

Para mais informações, entre em contato com a equipe de segurança de TI da sua organização.

# Contraparte

Considera-se contraparte qualquer entidade ou usuário que interaja com os recursos da plataforma. Por exemplo:

- **Acesso a um Tutorial:** A contraparte é o usuário que está acessando o tutorial.
- **Participação em um Curso:** A contraparte é o aluno inscrito no curso.

A plataforma registra todas as informações relevantes sobre a contraparte para garantir a integridade dos dados e fornecer uma experiência personalizada aos usuários.

#### Informações que podem ser registradas na contraparte:

- **Tipo de Conta:** Conta de aluno, conta de instrutor, etc.
- **Identificador do Usuário:** UUID único do usuário.
- **Nome do Usuário:** Nome completo do usuário.
- **Email do Usuário:** Endereço de email do usuário.
- **Tipo de Acesso:** Tipo de recurso acessado (tutorial, curso, artigo, etc.).

Contato para suporte adicional: suporte@plataformadeaprendizado.com