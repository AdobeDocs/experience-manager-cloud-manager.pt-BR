---
title: Notas da versão 2023.10.0
description: Estas são as notas de versão do Cloud Manager 2023.10.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: a5a304541409bc1775090eef2a669e1e0bcf005e
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 58%

---


# Notas de versão do Cloud Manager 2023.10.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2023.10.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Notas de versão atuais do Cloud Manager no AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=pt-BR)

## Data de lançamento {#release-date}

A data de lançamento da versão 2023.10.0 do [!UICONTROL Cloud Manager] é 5 de outubro de 2023. A próxima versão está planejada para 2 de novembro de 2023.

## Novidades {#what-is-new}

* A variável **Gerente de implantação** pode [configure um conjunto de caminhos de conteúdo que serão invalidados ou removidos do cache do Dispatcher do AEM quando um pipeline de não produção for executado.](/help/using/non-production-pipelines.md)
   * Essas ações de cache serão executadas como parte da etapa do pipeline de implantação, logo após a implantação de qualquer pacote de conteúdo.
   * Essas configurações usam o comportamento padrão do Dispatcher do AEM.
* Com a versão de outubro de 2023 do Cloud Manager, as versões do Java estão sendo atualizadas por meio de uma implantação em fases.
   * As versões do Java estão sendo atualizadas para o Oracle JDK 8u371 e o Oracle JDK 11.0.20.
   * [Consulte a supervisão do OpenJDK](https://openjdk.org/groups/vulnerability/advisories/) para obter detalhes sobre a segurança e correções de erros nessas atualizações do JDK.
