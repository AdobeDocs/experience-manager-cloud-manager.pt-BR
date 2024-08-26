---
title: Notas de versão do Cloud Manager 2024.8.0
description: Estas são as notas de versão do Cloud Manager 2024.8.0.
feature: Release Information
source-git-commit: 5ced643fabe0a670e456cbea72f9da8196ac774a
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 21%

---


# Notas de versão do Cloud Manager 2024.8.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2024.8.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Cloud Manager nas notas de versão atuais do AEM as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Data de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] 2024.8.0 é quinta-feira, 14 de agosto de 2024. A próxima versão está planejada para 11 de agosto de 2022.

## Novidades {#what-is-new}

* Para pipelines somente de preparo e somente de produção (disponíveis como parte do [programa de adoção antecipada](#staging-production-only-pipelines)), agora você pode executá-los no [modo de emergência](/help/using/stage-prod-only.md#emergency-mode), ignorando o teste de preparo.

## Programa de adoção antecipada {#early-adoption}

Faça parte do programa de adoção antecipada da Cloud Manager e tenha a chance de testar alguns recursos futuros.

### Pipelines somente de preparo e somente produção {#staging-production-only-pipelines}

A Adobe está animada em anunciar a introdução do suporte para [pipelines somente de preparo e somente de produção](/help/using/stage-prod-only.md). Esse novo recurso permite dividir os pipelines de implantação de produção de pilha completa em implantações menores e mais especializadas.

Se você quiser testar este recurso e fornecer feedback, envie um email para `Grp-cloudmanager_splitpipelines@adobe.com` usando o endereço de email associado à sua Adobe ID.

## Correções de erros

* Um problema raro foi corrigido em que as etapas do pipeline eram executadas após a exclusão do pipeline.
* A reexecução do pipeline agora funciona na primeira tentativa, corrigindo um problema raro em que uma nova execução tinha que ser iniciada várias vezes.
* As etapas de implantação agendadas para pipelines de pilha completa agora respeitam a data agendada selecionada e não revertem para **Agora**.
* Os status das tarefas de conteúdo de cópia com falha agora são refletidos corretamente e não mostram mais um status `In Progress` incorretamente em raras circunstâncias.

## Problemas conhecidos {#known-issues}

{{content-copy-known-issues}}
