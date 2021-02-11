---
title: Pipeline de CI/CD
seo-title: Pipeline de CI/CD
description: Visão geral do CI/CD Pipeline, que lida com as implantações no palco e na produção no Cloud Manager
seo-description: Siga esta seção para saber mais sobre o pipeline de CI/CD, que lida com as implantações no palco e produção no Cloud Manager
uuid: 763ddb24-05cd-463f-8d72-a2e69bbe6b7e
topic-tags: introduction
discoiquuid: 1cdb76eb-1a91-4689-8579-0fa9fccc0592
translation-type: tm+mt
source-git-commit: 2dda85baa5e7ed9bfd8933df3580ec6fc3c210fd
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---


# Pipeline de CI/CD {#ci-cd-pipeline}

## Visão geral do pipeline {#pipeline-overview}

[!UICONTROL Cloud Manager] inclui uma estrutura de integração contínua (CI) e Delivery contínuo (CD) que permite que as equipes de implementação testem e distribuam rapidamente códigos novos ou atualizados. Por exemplo, as equipes de implementação podem configurar, configurar e start um pipeline de CI/CD automatizado que aproveita as práticas recomendadas de codificação de Adobe para executar uma varredura de código completa e garantir a mais alta qualidade do código.

O pipeline de CI/CD também automatiza os processos de teste de unidade e desempenho para aumentar a eficiência da implantação e identificar proativamente problemas críticos que são dispendiosos de corrigir após a implantação. As equipes de implementação podem acessar um relatório abrangente de desempenho de código para obter visibilidade sobre o impacto potencial nos KPIs e validações críticas de segurança se o código for implantado na produção.

## Processo de pipeline {#pipeline-process}

O diagrama a seguir ilustra o que acontece quando uma versão é acionada em [!UICONTROL Cloud Manager]. A tabela que acompanha explica cada etapa do fluxo de trabalho.

![](assets/screen_shot_2018-05-30at82457pm.png)

A tabela a seguir detalha o que está acontecendo durante cada etapa do processo:

| Etapa do processo de pipeline | O que está acontecendo? |
|---|---|
| 1. Start de uma versão | Um gerenciador de implantação aciona uma versão manualmente, com uma confirmação Git ou com base em uma programação recorrente. |
| 2. Criar etiqueta de versão | [!UICONTROL Cloud Manager] cria uma tag Git para marcar a versão usando um número de versão gerado automaticamente. Por exemplo: 2018.531.245527.00000122 |
| 3. Criado como versão com versão gerada automaticamente | [!UICONTROL Cloud Manager] cria o aplicativo com o número de versão atribuído recentemente. |
| 4. Avaliar a qualidade do código | [!UICONTROL Cloud Manager] verifica o código fonte e fornece um resumo antes que o código possa ser implantado no ambiente stage |
| 5. Artefato(s) com versão armazenada | Os artefatos de versão são armazenados para uso posterior nas etapas de implantação. |
| 6. Implantação automática do(s) artefato(s) para a fase AEM AMS | O artefato de lançamento é implantado no ambiente stage. |
| 7. Acionar testes automatizados | [!UICONTROL Cloud Manager] executa os testes de Desempenho e Segurança no artefato. |
| 8. Implantação do Acionador de Produção | Depois que os testes automatizados forem concluídos, [!UICONTROL Cloud Manager] start a implantação para a produção. |
| 9. [!UICONTROL Cloud Manager] obtém Artefatos para implantação | [!UICONTROL Cloud Manager] puxa os artefatos de versão armazenados. |
| 10. Propagar artefatos para a produção | Os artefatos de lançamento são implantados no ambiente Produção. |

### Como configurar um pipeline CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para saber mais sobre a configuração de pipeline, consulte [configurar pipeline](configuring-pipeline.md).

## Portas de qualidade {#quality-gates}

O pipeline de CI/CD fornece portas de qualidade ou critérios de aceitação, que devem ser cumpridos antes que o código possa ser movido do ambiente stage para o ambiente de implantação. Há três portões no pipeline:

* Qualidade do código
* Teste de desempenho
* Teste de segurança

Para cada uma dessas portas, há três níveis de problemas identificados:

* **Questões críticas**  identificadas pela porta que causam uma falha imediata do pipeline.
* **Importante**  - problemas identificados pela porta que fazem com que o pipeline entre em estado de pausa. Um gerente de implantação, gerente de projeto ou proprietário de negócios pode substituir os problemas, caso em que o pipeline continua, ou pode aceitar os problemas, caso em que o pipeline pára com uma falha.
* **Informações**  - questões identificadas pela porta, que são fornecidas exclusivamente para fins informativos e não têm impacto na execução do gasoduto.

Este é um exemplo de uma verificação de código com problemas identificados para o código:

![](assets/quality-gate-failed.png)

### Como configurar portas {#how-to-setup-gates}

Consulte **[Configurando Gates](configuring-pipeline.md)** para obter detalhes sobre como configurar seu código, suas portas de qualidade e desempenho.
