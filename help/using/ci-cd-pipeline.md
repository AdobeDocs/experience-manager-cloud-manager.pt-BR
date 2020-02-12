---
title: Pipeline de CI/CD
seo-title: Pipeline de CI/CD
description: 'null'
seo-description: Siga esta seção para saber mais sobre o pipeline de CI/CD, que lida com implantações para o palco e produção no Cloud Manager.
uuid: 763ddb24-05cd-463f-8d72-a2e69bbe6b7e
topic-tags: introduction
discoiquuid: 1cdb76eb-1a91-4689-8579-0fa9fccc0592
translation-type: tm+mt
source-git-commit: 8580cec50ac5dafb4e2525371a39d58c82f1cbc9

---


# Pipeline de CI/CD {#ci-cd-pipeline}

## Visão geral do pipeline {#pipeline-overview}

[!UICONTROL Cloud Manager] inclui uma estrutura de integração contínua (CI) e entrega contínua (CD) que permite que as equipes de implementação testem e distribuam rapidamente códigos novos ou atualizados. Por exemplo, as equipes de implementação podem configurar, configurar e iniciar um pipeline de CI/CD automatizado que aproveita as práticas recomendadas de codificação da Adobe para executar uma verificação completa de código e garantir a mais alta qualidade.

O pipeline de CI/CD também automatiza os processos de teste de unidade e desempenho para aumentar a eficiência da implantação e identificar proativamente problemas críticos que são dispendiosos de corrigir após a implantação. As equipes de implementação podem acessar um relatório abrangente de desempenho de código para obter visibilidade sobre o impacto potencial nos KPIs e validações críticas de segurança se o código for implantado na produção.

## Processo de Pipeline {#pipeline-process}

O diagrama a seguir ilustra o que acontece quando uma liberação é acionada em [!UICONTROL Cloud Manager]. A tabela que acompanha explica cada etapa do fluxo de trabalho.

![](assets/screen_shot_2018-05-30at82457pm.png)

A tabela a seguir detalha o que ocorre durante cada etapa do processo:

| Etapa do processo de pipeline | O que está acontecendo? |
|---|---|
| 1. Iniciar uma versão | Um gerenciador de implantação aciona uma versão manualmente, com uma confirmação Git ou com base em uma programação recorrente. |
| 2. Criar etiqueta de versão | [!UICONTROL Cloud Manager] cria uma tag Git para marcar a versão usando um número de versão gerado automaticamente. Por exemplo: 2018.531.245527.00000122 |
| 3. Criado como versão com versão gerada automaticamente | [!UICONTROL Cloud Manager] cria o aplicativo com o número de versão atribuído recentemente. |
| 4. Avaliar a qualidade do código | [!UICONTROL Cloud Manager] verifica o código fonte e fornece um resumo antes que o código possa ser implantado no ambiente do estágio |
| 5. Artefato(s) com versão armazenada | Os artefatos de versão são armazenados para uso posterior nas etapas de implantação. |
| 6. Implantação automática de artefato(s) no AEM Stage | O artefato de lançamento é implantado no ambiente de estágio. |
| 7. Acionar testes automatizados | [!UICONTROL Cloud Manager] executa os testes de Desempenho e Segurança no artefato. |
| 8. Implantação do acionador de produção | Após a conclusão dos testes automatizados, [!UICONTROL Cloud Manager] a implantação é iniciada para produção. |
| 9. [!UICONTROL Cloud Manager] obtém Artefatos para implantação | [!UICONTROL Cloud Manager] puxa os artefatos de versão armazenados. |
| 10. Propagar artefatos à produção | Os artefatos de lançamento são implantados no ambiente de produção. |

### Como configurar um pipeline de CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para saber mais sobre a configuração de pipeline, consulte [configuração de pipeline](configuring-pipeline.md).

## Portas de qualidade {#quality-gates}

O pipeline de CI/CD fornece portas de qualidade, ou critérios de aceitação, que devem ser cumpridos antes que o código possa ser movido do ambiente de estágio para o ambiente de implantação. Há três portões no pipeline:

* Qualidade do código
* Teste de desempenho
* Teste de segurança

Para cada uma dessas portas, há três níveis de problemas identificados:

* **Questões críticas** identificadas pela porta que causam uma falha imediata do pipeline.
* **Importante** - problemas identificados pela porta que fazem com que o pipeline entre em estado de pausa. Um gerente de implantação, gerente de projeto ou proprietário de negócios pode substituir os problemas, caso em que o pipeline continua, ou pode aceitar os problemas, caso em que o pipeline pára com uma falha.
* **Informação** - questões identificadas pela porta que são fornecidas exclusivamente para fins informativos e que não têm impacto na execução do gasoduto.

Este é um exemplo de uma verificação de código com problemas identificados para o código:

![](assets/quality-gate-failed.png)

### Como configurar portas {#how-to-setup-gates}

Consulte **[Configuração de portões](configuring-pipeline.md)**para obter detalhes sobre como configurar seu código, suas portas de qualidade e desempenho.
