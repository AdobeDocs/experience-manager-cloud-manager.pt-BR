---
title: Repositório de código-fonte
seo-title: Repositório de código-fonte do Adobe AEM Cloud Manager
description: Siga esta página para saber mais sobre o repositório Git provisionado para cada programa que você tem no Cloud Manager.
seo-description: Siga esta página para saber mais sobre o repositório Git provisionado para cada programa que você tem no Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
feature: Provisioning
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 2%

---


# Repositório de código-fonte {#source-code-repository}

## Repositório do Cloud Manager {#cloud-manager-repository}

Sua assinatura [!UICONTROL AEM Managed Services] incluirá um repositório de código-fonte provisionado e gerenciado pelo Adobe. Cada programa de cliente recebe um único e exclusivo **Repositório Git**, onde seu código associado será armazenado e protegido.

Como prática recomendada, você sempre deve usar o Repositório Git do Cloud Manager, que fica vazio sem ramificações configuradas ou projetos de amostra. Para usar o Repositório Git do Cloud Manager, você receberá um **token de acesso privado** que permitirá usar qualquer cliente compatível com Git para criar ramificações, armazenar e recuperar seu código, listar o histórico de commit etc.

Para obter mais informações sobre como configurar ramificações no Git, consulte [Configuração das Ramificações de Liberação](configure-your-release-branches.md).

Para obter mais informações sobre como usar o **Repositório Git do Cloud Manager** com o pipeline de CI/CD, consulte [Configuração do pipeline de CI/CD](configuring-pipeline.md).

## Repositório local {#on-premise-repository}

Em alguns casos, você terá um Repositório Git existente e deseja continuar usando. Nesses casos, você pode usar o recurso suportado do Git para vários repositórios remotos. O desenvolvimento diário continuaria acontecendo no Repositório Git. Quando uma ramificação de versão estiver pronta para uma implantação em produção, você enviará seu código mais recente para o repositório Git do Cloud Manager e acionará o pipeline de CI/CD do Cloud Manager.

>[!NOTE]
>
>Para visualizar os comandos Git comuns, consulte o [Git Cheat](https://education.github.com/git-cheat-sheet-education.pdf).

