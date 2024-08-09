---
title: Notas da versão 2024.7.0
description: Saiba mais sobre as notas de versão do Cloud Manager 2024.7.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 4%

---


# Notas de versão do Cloud Manager 2024.7.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2024.7.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Cloud Manager nas notas de versão atuais do AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Data de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] 2024.7.0 é 18 de julho de 2024. A próxima versão está planejada para 13 de agosto de 2024.

## Novidades {#what-is-new}

* O [pipeline de produção](/help/using/production-pipelines.md#adding-production-pipeline) e o [pipeline de não produção](/help/using/non-production-pipelines.md#adding-non-production-pipeline) acionam **Alterações no Git** para iniciar o pipeline em uma confirmação agora estão disponíveis para [repositórios privados](/help/managing-code/private-repositories.md).
* Um pipeline de pré-produção só pode ser acionado manualmente e não pode ser configurado como **Em Alterações do Git**.
* Para pipelines somente de produção, a lista de execuções promovíveis inclui execuções com uma versão de artefato maior que a versão de artefato implantada no ambiente de produção.
* [O Arquétipo de Projeto AEM](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/developing/archetype/overview) foi atualizado para a [versão 49](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49).

## Programa de adoção antecipada {#early-adoption}

Fazer parte do programa de adoção antecipada da Cloud Manager e testar alguns recursos futuros

### Pipelines somente de preparo e somente de produção {#staging-production-only-pipelines}

O suporte para [pipelines somente de preparo e somente de produção](/help/using/stage-prod-only.md) foi introduzido, permitindo dividir os pipelines de implantação de produção de pilha completa em implantações menores e especializadas.

Se você estiver interessado em testar este novo recurso e compartilhar seus comentários, envie um email para `Grp-cloudmanager_splitpipelines@adobe.com` por meio de seu endereço de email associado à sua Adobe ID.
