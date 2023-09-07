---
title: Notas da versão 2023.9.0
description: Estas são as notas de versão do Cloud Manager 2023.9.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 74381d5d154f7c61135a990d2806fa9e39be7690
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 54%

---


# Notas de versão do Cloud Manager 2023.9.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2023.9.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Notas de versão atuais do Cloud Manager no AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=pt-BR)

## Data de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] versão 2023.9.0 é 7 de setembro de 2023. A próxima versão está planejada para 5 de outubro de 2023.

## Novidades {#what-is-new}

Esta versão contém correções de erros.

## Correções de erros {#bug-fixes}

* Quando um programa é excluído, qualquer pipeline associado em execução também é excluído, garantindo que o pipeline não seja designado incorretamente como status de falha.
* Ocasionalmente, quando todas as etapas de uma execução de pipeline são &#39;concluídas&#39;, o status do pipeline é visto como &quot;em execução&quot;, fazendo parecer que está em um estado travado. Agora é visto como &#39;Concluído&#39;.
* Para ramificações de repositório geradas usando o arquétipo do gerador de código, ocorre falha no pipeline de CI/CD.
