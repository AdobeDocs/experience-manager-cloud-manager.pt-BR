---
title: Notas da versão 2024.7.0
description: Estas são as notas de versão do Cloud Manager 2024.7.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: d7c4c87bbc3c66ca9517c4d0c97e25a2302e1e8a
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 96%

---


# Notas de versão do Cloud Manager 2024.7.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2024.7.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Notas de versão atuais do Cloud Manager no AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=pt-BR)

## Data de lançamento {#release-date}

A data de lançamento da versão 2024.7.0 do [!UICONTROL Cloud Manager] é 18 de julho de 2024. A próxima versão está planejada para 12 de agosto de 2024.

## Novidades {#what-is-new}

* O acionador **Sobre alterações do Git** do [pipeline de produção](/help/using/production-pipelines.md#adding-production-pipeline) e do [pipeline de não produção](/help/using/non-production-pipelines.md#adding-non-production-pipeline) para iniciar o pipeline em uma confirmação agora estão disponíveis para [repositórios privados.](/help/managing-code/private-repositories.md)
* Um pipeline de pré-produção só pode ser acionado manualmente e não pode ser configurado como **Sobre alterações do Git**.
* Para pipelines somente de produção, a lista de execuções promovíveis inclui aquelas que têm a versão do artefato maior que a versão do artefato implantada no ambiente de produção.
* [O arquétipo de projeto do AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=pt-BR) foi atualizado para a [versão 49.](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49)


## Programa de adoção antecipada {#early-adoption}

Faça parte de nosso programa de adoção antecipada e tenha a oportunidade de testar alguns recursos futuros

### Pipelines somente de preparo e somente de produção {#staging-production-only-pipelines}

O suporte para [pipelines somente de preparo e somente de produção](/help/using/stage-prod-only.md) foi introduzido, permitindo dividir os pipelines de implantação de produção de pilha completa em implantações menores e especializadas.

Se tiver interesse em testar esse novo recurso e compartilhar seu feedback, envie um email para `Grp-cloudmanager_splitpipelines@adobe.com` utilizando o endereço de email associado à sua Adobe ID.
