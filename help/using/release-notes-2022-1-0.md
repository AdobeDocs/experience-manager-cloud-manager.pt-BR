---
title: Notas da versão 2022.01.0
description: Estas são as notas de versão do Cloud Manager versão 2022.01.0.
feature: Release Information
source-git-commit: 099a4490e3a8578b9f3485fd1514d1e97db977ab
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 6%

---

# Notas de versão do Cloud Manager versão 2021.12.0 {#release-notes}

A seção a seguir descreve as notas de versão gerais de [!UICONTROL Cloud Manager] versão 2022.01.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager AEM as a Cloud Service, consulte [Cloud Manager nas notas de versão atuais AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data de lançamento {#release-date}

A data de lançamento de [!UICONTROL Cloud Manager] a versão 2022.01.0 é 20 de janeiro de 2022. A próxima versão está planejada para 10 de fevereiro de 2022.

## Novidades {#whats-new}

* O Cloud Manager [evite reconstruir a base de código quando detecta que a mesma confirmação de git é usada](/help/using/setting-up-project.md#build-artifact-reuse) em várias execuções completas de pipeline de pilha.
* Após gerar uma senha git, a data de expiração será exibida.

## Correções de erros {#bug-fixes}

* Ocorrências pouco frequentes de falhas de pipeline falso positivo foram endereçadas.
* Para programas com apenas um repositório, a tela de execução do pipeline agora exibirá o nome do repositório.
