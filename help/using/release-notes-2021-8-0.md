---
title: Notas da versão 2021.8.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.8.0
feature: Release Information
source-git-commit: 3fccb0b577662ebc12b65777cbf9624e06d4259d
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 7%

---

# Notas da versão 2021.8.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2021.8.0.

>[!NOTE]
>Consulte [Notas de versão atuais](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) para ver as notas de versão mais recentes do Cloud Manager no AEM como um Cloud Service.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2021.8.0 é 12 de agosto de 2021.[!UICONTROL Cloud Manager]


## Novidades {#whats-new}

* Capacidade de autoatendimento para permitir que os usuários criem e gerenciem vários repositórios por meio da interface do usuário do Cloud Manager.

* SonarQube estava lendo desnecessariamente os dados do histórico de git. Em bases de código grandes, isso poderia resultar em uma penalidade desnecessária no desempenho da build.

* Agora há uma API disponível para invalidar o cache de dependência Maven por pipeline.

* A versão do AEM Project Archetype usada pelo Cloud Manager foi atualizada para a versão 29.

## Correções de erros {#bug-fixes}

* Ocasionalmente, quando um pipeline é acionado duas vezes por algum motivo, resulta em uma das execuções falhando com o erro *cannot update pipeline execution status* .
