---
title: Notas da versão para 2022.5.0
description: Estas são as notas de versão do Cloud Manager versão 2022.5.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 0ddfd152cb15731882d198d043dd8897b5073ab4
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 46%

---


# Notas de versão do Cloud Manager versão 2022.5.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] versão 2022.5.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager AEM as a Cloud Service, consulte [Cloud Manager nas notas de versão atuais AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data de lançamento {#release-date}

A data de lançamento de [!UICONTROL Cloud Manager] a versão 2022.5.0 é 5 de maio de 2022. A próxima versão está planejada para 9 de junho de 2022.

## Novidades {#what-is-new}

O acesso ao registro do Ambiente de AEM pode ser feito usando a função Desenvolvedor .

## Correções de erros {#bug-fixes}

* Um subconjunto de repositórios Git criados manualmente tinha um valor de nome incorreto que impedia que o recurso de reutilização de artefato de build fosse efetivo. Os nomes desses repositórios foram alterados e os usuários verão o nome corrigido na API/interface do Cloud Manager.
* Os artefatos de build dos pipelines de não produção eram reutilizados inadequadamente em pipelines de pilha completa de produção.
* Ao adicionar ou editar um pipeline de qualidade de código, as opções para lidar com falhas de métrica não são mais exibidas.
* Algumas configurações inesperadas de variável de pipeline podem causar erros na etapa de build.
