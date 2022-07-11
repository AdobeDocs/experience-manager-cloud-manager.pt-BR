---
title: Notas da versão para 2022.6.0
description: Estas são as notas de versão do Cloud Manager versão 2022.6.0.
feature: Release Information
source-git-commit: f202b245f35bcffa56b43f26a13b97d42fdb474e
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 3%

---


# Notas de versão do Cloud Manager versão 2022.6.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] versão 2022.6.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager AEM as a Cloud Service, consulte [Cloud Manager nas notas de versão atuais AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data de lançamento {#release-date}

A data de lançamento de [!UICONTROL Cloud Manager] a versão 2022.6.0 é 9 de junho de 2022. A próxima versão está prevista para 30 de junho de 2022.

## Novidades {#what-is-new}

* Um novo cartão de boas-vindas na página de aterrissagem do Cloud Manager fornece aos usuários acesso rápido a tutoriais de integração e métricas de progresso relacionadas ao locatário.
   * Esse recurso será implementado em uma abordagem em fases na semana seguinte à versão 2022.06.0.
* [Os artefatos da build agora podem ser reutilizados](/help/using/setting-up-project.md#build-artifact-reuse) ao usar o espelhamento de git.

## Alterações na API {#api-changes}

* O [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms) A API foi substituída e [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) deve ser usada em vez disso.
   * `List Programs` continua a funcionar, mas seu uso gerará mensagens de aviso em logs.
   * Ele não será mais suportado após três meses.