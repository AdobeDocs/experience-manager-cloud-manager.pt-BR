---
title: Repositório de código-fonte
seo-title: Repositório de código fonte para o Adobe AEM Cloud Manager
description: Siga esta página para saber mais sobre o repositório git provisionado para cada programa que você possui no Cloud Manager.
seo-description: Siga esta página para saber mais sobre o repositório git provisionado para cada programa que você possui no Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
translation-type: tm+mt
source-git-commit: 697311cd00ef96568f6befd2fe76febafc27961e
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 2%

---


# Repositório de código-fonte {#source-code-repository}

## Cloud Manager Repository {#cloud-manager-repository}

Sua [!UICONTROL AEM Managed Services] subscrição incluirá um repositório de código fonte provisionado e gerenciado pelo Adobe. A cada programa do cliente é atribuído um único repositório **** Git exclusivo, no qual o código associado será armazenado e protegido.

Como prática recomendada, você deve sempre usar o Repositório Git do Gerenciador de nuvem, que fica vazio sem ramificações configuradas ou projetos de amostra. Para usar o Repositório Git do Cloud Manager, você receberá um token de acesso **** privado que permitirá que você use qualquer cliente compatível com Git para criar ramificações, armazenar e recuperar seu código, lista o histórico de confirmação etc.

Para obter mais informações sobre como configurar ramificações no Git, consulte [Configuração das Ramificações](configure-your-release-branches.md)de Liberação.

Para obter mais informações sobre como usar o Repositório **Git do Cloud Manager com o Pipeline CI/CD, consulte** Configuração do pipeline [](configuring-pipeline.md)CI/CD.

## Repositório local {#on-premise-repository}

Em alguns casos, você terá um Repositório Git existente e deseja continuar usando-o. Nesses casos, você pode usar o recurso compatível com Git para vários repositórios remotos. O desenvolvimento cotidiano continuaria a ocorrer no seu Repositório Git. Quando uma ramificação de lançamento estiver pronta para uma implantação para produção, você encaminhará seu código mais recente para o repositório Git do Cloud Manager e acionará o pipeline CI/CD do Cloud Manager.

>[!NOTE]
>
>Para visualização dos comandos Git comuns, consulte a Folha [](https://education.github.com/git-cheat-sheet-education.pdf)Git Cheat.

