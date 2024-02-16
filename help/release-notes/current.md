---
title: Notas da versão 2024.2.0
description: Estas são as notas de versão do Cloud Manager 2024.2.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 524471a87217c15dae96c3e6aee57426b43dcccb
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 61%

---


# Notas de versão do Cloud Manager 2024.2.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2024.2.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Notas de versão atuais do Cloud Manager no AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=pt-BR)

## Data de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] A versão 2024.2.0 é 16 de fevereiro de 2024. A próxima versão está planejada para 16 de março de 2024.

## Novidades {#what-is-new}

* Como parte da [implantação,](/help/using/code-deployment.md) o cache do Dispatcher foi liberado no **Anexar Dispatcher** etapa. Para permitir que você teste as alterações em cada nó antes de anexá-lo ao balanceador de carga do aplicativo, após implantar o código em um determinado editor, agora é possível testar as alterações diretamente do Dispatcher associado antes de anexar esse Dispatcher ao balanceador de carga.
* [O ambiente de criação](/help/getting-started/build-environment.md) foi atualizado para Maven versão 3.9.4 e versões do JDK jdk-11.0.22 e jdk1.8.0_401.

## Programa de adoção antecipada {#early-adoption}

Faça parte de nosso programa de adoção antecipada e tenha a oportunidade de testar alguns recursos futuros

### Traga seu próprio GitHub {#byo-github}

Se você usa o GitHub para gerenciar repositórios, [agora é possível validar o código diretamente nos seus repositórios do GitHub por meio do Cloud Manager.](/help/managing-code/byo-github.md) Essa integração elimina a necessidade de sincronizar consistentemente o código com o repositório da Adobe e permite confirmar solicitações de “pull” antes de mesclá-las às ramificações principais. Esse recurso é exclusivo do GitHub público. A compatibilidade com o GitHub auto-hospedado não está disponível.

Se tiver interesse em testar esse novo recurso e compartilhar seu feedback, envie um email para `Grp-CloudManager_BYOG@adobe.com` utilizando o endereço de email associado à sua Adobe ID.

## Correções de erros {#bug-fixes}

* O JDK dos contêineres de build foi atualizado para uma versão que resolve [JDK-8313765.](https://bugs.openjdk.org/browse/JDK-8313765)
