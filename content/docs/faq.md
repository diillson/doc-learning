---
title: "FAQ"
description: "Perguntas frequentes"
icon: "quiz"
date: "2023-05-22T00:27:57+01:00"
lastmod: "2023-05-22T00:27:57+01:00"
draft: false
toc: true
weight: 800
---

### Estou tendo problemas ao utilizar um serviço AWS. O que devo fazer?

**Confira mais sobre a resolução de problemas em AWS na nossa [documentação de troubleshooting](docs/quickstart/troubleshooting/#aws-troubleshooting)!**

- Verifique se todas as permissões necessárias estão configuradas corretamente.
- Certifique-se de que os recursos estão dentro dos limites de serviço.
- Revise os logs do CloudWatch para identificar erros específicos.

Caso já tenha verificado as possibilidades acima e ainda não conseguiu solucionar seu problema, acione [suporte](docs/suporte) informando as seguintes informações:
  - Identificador do recurso
  - Mensagem de erro encontrada
  - Ambiente em que o problema ocorreu

### Por que meu deployment no Kubernetes está falhando?

Algum campo do seu manifesto Kubernetes pode estar fora dos padrões esperados. Revise os formatos dos campos enviados através da [documentação oficial do Kubernetes](https://kubernetes.io/docs/concepts/), corrija o campo fora do padrão e tente novamente.

Se não conseguir identificar o problema, acione o suporte com as seguintes informações:
- Identificador do cluster
- Logs do pod em falha
- Ambiente em que o deployment foi realizado

### Meu script Terraform está retornando erros. O que devo fazer?

Revise nossas recomendações de [boas práticas sobre scripts Terraform](docs/boas-praticas/#terraform-scripts).

- Certifique-se de que a sintaxe do HCL está correta.
- Verifique se todos os provedores e módulos necessários estão corretamente referenciados.
- Utilize o comando `terraform validate` para identificar possíveis problemas no script.

### Como solucionar problemas no ElasticSearch?

Siga as instruções disponíveis em nossa [página de troubleshooting do ElasticSearch](docs/features/elasticsearch-troubleshooting).

- Verifique o status do cluster e dos nós.
- Analise os logs do ElasticSearch para identificar erros específicos.
- Certifique-se de que os índices estão corretamente configurados e sem sobrecarga.

### Qual é a melhor prática para monitoramento com Splunk?

Em nossa [documentação de Splunk](docs/features/splunk-monitoring), você encontrará dicas e melhores práticas para configurar e utilizar o Splunk.

- Configure inputs para capturar todos os dados relevantes.
- Crie dashboards personalizados para visualização rápida de métricas chave.
- Utilize alertas para monitorar eventos críticos em tempo real.

### Como configurar e usar Apache Kafka?

Revise a [documentação de configuração do Kafka](docs/features/kafka-setup) para garantir que todos os componentes estão configurados corretamente.

- Verifique a configuração dos brokers e zookeepers.
- Certifique-se de que os tópicos estão corretamente criados e particionados.
- Monitore o desempenho dos consumidores e produtores para identificar gargalos.

### Qual o horário de suporte para a plataforma de aprendizado?

Nosso suporte está disponível **24h/7d** para questões críticas.

Para questões de desenvolvimento e suporte não-crítico, nosso horário de atendimento é **das 8h às 18h em dias úteis**. Caso necessite de suporte fora desse horário, por favor, entre em contato previamente através do [canal de suporte](/docs/suporte).
