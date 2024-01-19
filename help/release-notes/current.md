---
title: Notas da versão 2024.1.0
description: Estas são as notas de versão do Cloud Manager 2024.1.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b235e398b42e9da3dd2efacdc0ef38b6803bd213
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 68%

---


# Notas de versão do Cloud Manager 2024.1.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2024.1.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Notas de versão atuais do Cloud Manager no AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=pt-BR)

## Data de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] A versão 2024.1.0 é 17 de janeiro de 2024. A próxima versão está planejada para 16 de fevereiro de 2024.

## Programa de adoção antecipada {#early-adoption}

Faça parte de nosso programa de adoção antecipada e tenha a oportunidade de testar alguns recursos futuros

### Traga seu próprio GitHub {#byo-github}

Se você usa o GitHub para gerenciar repositórios, [agora é possível validar o código diretamente nos seus repositórios do GitHub por meio do Cloud Manager.](/help/managing-code/byo-github.md) Essa integração elimina a necessidade de sincronizar consistentemente o código com o repositório da Adobe e permite verificar solicitações “pull” antes de mesclá-las às ramificações principais.

Se tiver interesse em testar esse novo recurso e compartilhar seu feedback, envie um email para `Grp-CloudManager_BYOG@adobe.com` utilizando o endereço de email associado à sua Adobe ID.

## Correções de erros {#bug-fixes}

* Um erro foi corrigido para alguns casos de canto em que os downloads falhavam devido a como o aplicativo de teste interpreta os dados, fazendo com que a porcentagem total de erros falhasse no teste.
* Quando uma etapa de criação termina com o status `FAILED` devido a uma `BUILD_MAVEN_TRANSFER_ARTIFACT_ERROR`, agora ele é descrito corretamente como um erro devido a conflitos de mesclagem com a ramificação de destino.
