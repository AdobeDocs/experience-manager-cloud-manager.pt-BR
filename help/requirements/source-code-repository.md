---
title: Repositório de código-fonte
description: Saiba mais sobre o repositório Git provisionado para cada programa que você tem no Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 20%

---


# Repositório de código do Source {#source-code-repository}

Saiba mais sobre o repositório Git provisionado para cada programa que você tem no Cloud Manager.

## Repositório do Cloud Manager {#cloud-manager-repository}

Sua assinatura do [!UICONTROL AEM Managed Services] inclui um repositório de código-fonte provisionado e gerenciado pela Adobe. Cada programa recebe um único repositório Git exclusivo, onde seu código associado é armazenado e protegido.

Como prática recomendada, você sempre deve usar o repositório Git da Cloud Manager, que fica vazio sem ramificações configuradas ou projetos de amostra. O Cloud Manager fornece um token de acesso privado para o repositório Git, permitindo que você use qualquer cliente Git para criar ramificações, gerenciar código, recuperar o histórico de confirmação e muito mais.

Para obter mais informações sobre como configurar ramificações no Git, consulte [Configurando ramificações de versão](/help/getting-started/configuring-branches.md).

Para obter mais informações sobre como usar o repositório Git do Cloud Manager com o pipeline de CI/CD, consulte [Configurar pipelines de produção](/help/using/production-pipelines.md) e [Configurar pipelines de não produção](/help/using/non-production-pipelines.md) para saber mais.

## Repositório no local {#on-premise-repository}

Você pode ter um repositório Git existente e querer continuar usando-o, nesse caso, você pode usar o recurso do Git para vários repositórios remotos. O desenvolvimento diário continuaria ocorrendo no repositório Git. Quando uma ramificação de versão estiver pronta para implantação em produção, você poderá enviar seu código mais recente para o repositório Git da Cloud Manager e acionar o pipeline de CI/CD do Cloud Manager.

Para ver comandos comuns do Git, consulte a [Folha de características do Git](https://education.github.com/git-cheat-sheet-education.pdf).
