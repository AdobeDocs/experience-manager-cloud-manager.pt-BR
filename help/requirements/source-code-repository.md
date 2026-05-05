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
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 100%

---

# Repositório de código-fonte {#source-code-repository}

Saiba mais sobre o repositório Git provisionado para cada programa que você tem no Cloud Manager.

## Repositório do Cloud Manager {#cloud-manager-repository}

Sua assinatura do [!UICONTROL AEM Managed Services] inclui um repositório de código-fonte provisionado e gerenciado pela Adobe. Cada programa recebe um único repositório Git exclusivo, onde seu código associado é armazenado e protegido.

Como prática recomendada, você sempre deve usar o repositório Git do Cloud Manager, que vem vazio sem ramificações configuradas ou projetos de amostra. O Cloud Manager fornece um token de acesso privado para o repositório Git, permitindo que você use qualquer cliente Git para criar ramificações, gerenciar código, recuperar o histórico de confirmações e muito mais.

Para mais informações sobre como configurar ramificações no Git, consulte [Configuração de ramificações de versão](/help/getting-started/configuring-branches.md).

Para mais informações sobre como usar o repositório Git do Cloud Manager com o pipeline de CI/CD, consulte [Configuração de pipelines de produção](/help/using/production-pipelines.md) e [Configuração de pipelines de não produção](/help/using/non-production-pipelines.md) para saber mais.

## Repositório no local {#on-premise-repository}

Você pode ter um repositório Git já existente e querer continuar usando-o, nesse caso você pode usar o recurso do Git para vários repositórios remotos. O desenvolvimento diário continuaria ocorrendo no seu repositório Git. Quando uma ramificação de versão estiver pronta para uma implantação em produção, você poderá enviar seu código mais recente para o repositório Git do Cloud Manager e acionar o pipeline de CI/CD do Cloud Manager.

Para ver comandos comuns do Git, consulte a [Folha de características do Git](https://education.github.com/git-cheat-sheet-education.pdf).
