---
title: Notas da versão para 2022.3.0
description: Estas são as notas de versão do Cloud Manager versão 2022.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 6e98f9d2fcd69799bad86d1e247212b26273bd0b
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 4%

---


# Notas de versão do Cloud Manager versão 2022.3.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] versão 2022.3.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager AEM as a Cloud Service, consulte [Cloud Manager nas notas de versão atuais AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data de lançamento {#release-date}

A data de lançamento de [!UICONTROL Cloud Manager] a versão 2022.3.0 é 10 de março de 2022. A próxima versão está planejada para 7 de abril de 2022.

## Novidades {#what-is-new}

* [O `reliability_rating` métrica crítica](understand-your-test-results.md) foi desativado.
* Agora, um usuário pode classificar as colunas na variável **Pipelines** no Cloud Manager.

## Correções de erros {#bug-fixes}

* [O **Ignorar alterações no Balanceador de Carga** opção](configuring-production-pipelines.md#adding-production-pipeline) pode ser desativado corretamente.
* [O **Ignorar alterações no Balanceador de Carga** opção](configuring-production-pipelines.md#adding-production-pipeline) agora é exibido para o workflow editar pipeline de implantação .
* Um subconjunto de repositórios git criados manualmente tinha valores de nome incorretos que afetavam [o recurso de reuso do artefato de compilação.](setting-up-project.md#build-artifact-reuse) Os nomes desses repositórios foram alterados e os usuários verão o nome corrigido na API/interface do usuário do Cloud Manager.
* [Ao adicionar ou editar um pipeline de qualidade de código,](configuring-non-production-pipelines.md) as opções para lidar com falhas de métrica não são mais exibidas.
* Configurações inesperadas de variável de pipeline não causam mais erros na etapa de build.
