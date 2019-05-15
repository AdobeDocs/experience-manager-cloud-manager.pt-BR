---
title: Pipeline CI/CD
seo-title: Pipeline CI/CD
description: 'null'
seo-description: Siga esta seção para saber mais sobre o pipeline CI/CD, que trata das implantações de estágio e produção no Experience Cloud Manager.
uuid: 763 ddb 24-05 cd -463 f -8 d 72-a 2 e 69 bbe 6 b 7 e
topic-tags: introdução
discoiquuid: 1 cdb 76 eb -1 a 91-4689-8579-0 fa 9 fccc 0592
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Pipeline CI/CD {#ci-cd-pipeline}

## Visão geral do pipeline {#pipeline-overview}

[!UICONTROL Cloud Manager] inclui uma estrutura de Integração contínua (CI) e de Entrega contínua (CD) que permite que as equipes de implementação testem e forneçam rapidamente um código novo ou atualizado. Por exemplo, as equipes de implementação podem configurar, configurar e iniciar um pipeline CI/CD automatizado que aproveita as práticas recomendadas de codificação da Adobe para executar um varredura de código minucioso e garantir a maior qualidade de código.

O pipeline CI/CD também automatiza os processos de teste de unidade e desempenho para aumentar a eficiência de implantação e identificar proativamente problemas críticos que são caros para corrigir após a implantação. As equipes de implementação podem acessar um relatório abrangente de desempenho de código para obter visibilidade sobre o impacto potencial em kpis e validações de segurança essenciais se o código for implantado na produção.

## Processo de pipeline {#pipeline-process}

O diagrama a seguir ilustra o que acontece quando uma versão é acionada [!UICONTROL Cloud Manager]. A tabela anexa explica cada etapa do fluxo de trabalho.

![](assets/screen_shot_2018-05-30at82457pm.png)

A tabela a seguir detalha o que está acontecendo durante cada etapa do processo:

| Etapa do processo do pipeline | O que está acontecendo? |
|---|---|
| 1. Iniciar uma versão | Um gerente de implantação aciona uma versão manualmente, com um compromisso Git ou com base em uma programação recorrente. |
| 2. Criar tag de lançamento | [!UICONTROL Cloud Manager] cria uma tag Git para marcar a versão usando um número de versão gerado automaticamente. Por exemplo: 2018.531.245527.0000001222 |
| 3. Criado como versão com a versão gerada automaticamente | [!UICONTROL Cloud Manager] cria o aplicativo com o número de versão recém-atribuído. |
| 4. Avaliar qualidade do código | [!UICONTROL Cloud Manager] verifica o código fonte e fornece um resumo antes que o código possa ser implantado no ambiente stage |
| 5. Artefato (s) de versão armazenado (s) | Os artefatos de lançamento são armazenados para uso posterior nas etapas de implantação. |
| 6. Implantação automática de artefatos para o AMS AEM Stage | O artefato de lançamento é implantado no ambiente stage. |
| 7. Acionar testes automatizados | [!UICONTROL Cloud Manager] executa os testes de Desempenho e Segurança no artefato. |
| 8. Implantação de acionador de produção | Depois que os testes automatizados forem concluídos [!UICONTROL Cloud Manager] , a implantação para produção será iniciada. |
| 9. [!UICONTROL Cloud Manager] Obtém artefatos para implantar | [!UICONTROL Cloud Manager] puxa os artefatos de versão armazenados. |
| 10. Artefatos deploráveis para Produção | Os artefatos de lançamento são implantados no ambiente de Produção. |

### Como configurar um pipeline CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para saber mais sobre a configuração do pipeline, consulte [Configurar pipeline](configuring-pipeline.md).

## Portfólios de qualidade {#quality-gates}

O Pipeline CI/CD fornece portfólios de qualidade, ou critérios de aceitação, que devem ser cumpridos antes que o código possa ser movido do ambiente stage para o ambiente de implantação. Há três passagens no pipeline:

* Qualidade do código
* Teste de desempenho
* Teste de segurança

Para cada uma dessas porturas, há três níveis de problemas identificados:

* **Crítica** - problemas identificados pela portão que causam uma falha imediata do pipeline.
* **Importante** - problemas identificados pela portão que fazem com que o pipeline insira um estado pausado. Um gerente de implantação, gerente de projeto ou proprietário de negócios pode substituir os problemas, nesse caso, o pipeline continua ou pode aceitar os problemas, e nesse caso o pipeline é interrompido com uma falha.
* **Informações** - problemas identificados pela portão que são fornecidos exclusivamente para fins informativos e não afetam a execução do pipeline.

A seguir está um exemplo de um Código Scan com problemas identificados para o código:

![](assets/quality-gate-failed.png)

### Como configurar passagens {#how-to-setup-gates}

Consulte **[Configuração de portfólio](configuring-pipeline.md)** para obter detalhes sobre como configurar seu código, qualidade e portfólio de desempenho.
