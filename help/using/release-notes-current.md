---
title: Notas da versão para 2022.5.0
description: Estas são as notas de versão do Cloud Manager versão 2022.5.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 84cc4352488002ad40102ea2c507af652d9012a1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 29%

---


# Notas de versão do Cloud Manager versão 2022.5.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2022.5.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service&#39;s current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data de lançamento {#release-date}

A data de lançamento de [!UICONTROL Cloud Manager] a versão 2022.5.0 é 5 de maio de 2022. A próxima versão está planejada para 9 de junho de 2022.

## Novidades {#what-is-new}

As solicitações HTTP de saída dos testes de ativos agora vêm de um intervalo IP fixo.

## Correções de erros {#bug-fixes}

* The &quot;Skip Load Balancer&quot; changes option was not able to be disabled.
* A opção Ignorar Alterações do Balanceador de Carga não era exibida no fluxo de trabalho de pipeline de edição de Implantação de Desenvolvimento do AMS.
* A subset of GIT repositories created manually had an incorrect name value which prevented the build artifact reuse feature from being effective. Os nomes desses repositórios foram alterados e os usuários verão o nome corrigido na API/interface do Cloud Manager.
* Os artefatos de build dos pipelines de não produção eram reutilizados inadequadamente em pipelines de pilha completa de produção.
* Ao adicionar ou editar um pipeline de qualidade de código, as opções para lidar com falhas de métrica não são mais exibidas.
* Some unexpected pipeline variable configurations could cause errors in the build step.
