---
title: Repositório de código-fonte
description: Saiba mais sobre o repositório Git provisionado para cada programa que você tem no Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: b24e9550f11486e7ed8da31d5da27f85ad5acaf2
workflow-type: tm+mt
source-wordcount: 236
ht-degree: 44%

---

# Repositório de código-fonte {#source-code-repository}

Saiba mais sobre o repositório Git provisionado para cada programa que você tem no Cloud Manager.

## Repositório do Cloud Manager {#cloud-manager-repository}

Sua assinatura do [!UICONTROL AEM Managed Services] inclui um repositório de código-fonte provisionado e gerenciado pela Adobe. Cada programa recebe um repositório Git exclusivo, onde seu código associado é armazenado e protegido.

Como prática recomendada, sempre use o repositório Git do Cloud Manager, que fica vazio, sem ramificações configuradas ou projetos de amostra. O Cloud Manager fornece um token de acesso privado para o repositório Git, permitindo que você use qualquer cliente Git para criar ramificações, gerenciar código, recuperar o histórico de confirmações e muito mais.

Para mais informações sobre como configurar ramificações no Git, consulte [Configuração de ramificações de versão](/help/getting-started/configuring-branches.md).

Para saber mais sobre como usar o repositório Git do Cloud Manager com o pipeline de CI/CD, consulte [Configurar pipeline de produção](/help/using/production-pipelines.md) e [Configurar pipeline de não produção](/help/using/non-production-pipelines.md).

## Repositório local {#on-premise-repository}

Se você tiver um repositório Git existente e quiser continuar usando-o, use o recurso do Git para vários repositórios remotos. O desenvolvimento continua no repositório Git. Quando uma ramificação de versão estiver pronta para implantação em produção, você poderá enviar seu código mais recente para o repositório Git do Cloud Manager e acionar o pipeline de CI/CD do Cloud Manager.

Para ver comandos comuns do Git, consulte o [Guia de Referência do Git](https://education.github.com/git-cheat-sheet-education.pdf).
