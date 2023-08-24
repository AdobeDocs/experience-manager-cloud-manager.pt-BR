---
title: Notas da versão 2023.8.0
description: Estas são as notas de versão do Cloud Manager 2023.8.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: f930f12b5f50dd96a1677ff7a56cf0e92a400556
workflow-type: ht
source-wordcount: '216'
ht-degree: 100%

---


# Notas de versão do Cloud Manager 2023.8.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2023.8.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Notas de versão atuais do Cloud Manager no AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=pt-BR)

## Data de lançamento {#release-date}

A data de lançamento da versão 2023.8.0 do [!UICONTROL Cloud Manager] é 10 de agosto de 2023. A próxima versão está planejada para 7 de setembro de 2023.

## Novidades {#what-is-new}

* Aprimoramentos foram feitos para facilitar a compreensão e melhorar a exibição de mensagens de erro na interface do Cloud Manager.

## Correções de erros {#bug-fixes}

* Casos pouco frequentes de travamento em processos de [cópia de conteúdo](/help/using/content-copy.md) foram resolvidos.
* Um problema de teste temporário foi resolvido para clientes que não usam o New Relic One.
* [As regras de qualidade do código personalizado](/help/using/custom-code-quality-rules.md) `SupportedRunmode` e `ImmutableMutableMixedPackage` foram removidas do SonarQube, pois são aplicáveis apenas ao AEM as a Cloud Service.
* Os usuários não encontrarão mais pipelines travados que parecem estar em estado de execução.
* O menu **Ambientes** agora fecha depois de acionar o modal **[Copiar conteúdo](/help/using/content-copy.md)**.
* [Uma reexecução de pipeline](/help/using/code-deployment.md#reexecute-deployment) não é mais permitida se a execução anterior não tiver um `commitId` definido no estado da fase de compilação.
* Uma mensagem mais compreensível agora é exibida para erros raros quando um usuário clica em um pipeline nas telas **Atividade** ou **Pipeline**.
