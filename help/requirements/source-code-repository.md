---
title: Repositório de código-fonte
description: Saiba mais sobre o repositório Git provisionado para cada programa que você tem no Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 2%

---


# Repositório de código-fonte {#source-code-repository}

Saiba mais sobre o repositório Git provisionado para cada programa que você tem no Cloud Manager.

## Repositório do Cloud Manager {#cloud-manager-repository}

Seu [!UICONTROL AEM Managed Services] a subscrição inclui um repositório de código-fonte provisionado e gerenciado pelo Adobe. Cada programa recebe um único repositório Git exclusivo, onde seu código associado será armazenado e protegido.

Como prática recomendada, você sempre deve usar o repositório Git do Cloud Manager, que fica vazio sem ramificações configuradas ou projetos de amostra. Para usar o repositório Git do Cloud Manager, você receberá um token de acesso privado que permitirá usar qualquer cliente Git para criar ramificações, armazenar e recuperar seu código, listar o histórico de commit etc.

Para obter mais informações sobre como configurar ramificações no git, consulte [Configurando Ramificações de Liberação.](/help/getting-started/configuring-branches.md)

Para obter mais informações sobre como usar o repositório Git do Cloud Manager com o pipeline de CI/CD, consulte os documentos [Configurar pipeline de produção](/help/using/production-pipelines.md) e [Configuração de pipeline de não produção](/help/using/non-production-pipelines.md) para saber mais.

## Repositório local {#on-premise-repository}

Você pode ter um repositório Git existente e deseja continuar usando, nesse caso, você pode usar o recurso do git para vários repositórios remotos. O desenvolvimento diário continuaria a ocorrer no repositório Git. Quando uma ramificação de versão estiver pronta para uma implantação em produção, você poderá enviar seu código mais recente para o repositório Git do Cloud Manager e acionar o pipeline de CI/CD do Cloud Manager.

Para ver comandos git comuns, consulte o [Folha de características do Git](https://education.github.com/git-cheat-sheet-education.pdf) no site do GitHub.
