---
title: Repositório de código-fonte
seo-title: Source Code Repository for Adobe AEM Cloud Manager
description: Siga esta página para saber mais sobre o repositório Git provisionado para cada programa que você tem no Cloud Manager.
seo-description: Follow this page to learn about the git repository that is provisioned for each program you have in Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
feature: Provisioning
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 2%

---

# Repositório de código-fonte {#source-code-repository}

## Repositório do Cloud Manager {#cloud-manager-repository}

Seu [!UICONTROL AEM Managed Services] a assinatura incluirá um repositório de código-fonte provisionado e gerenciado pelo Adobe. Cada programa de cliente recebe um único e único **Repositório Git**, onde seu código associado será armazenado e protegido.

Como prática recomendada, você sempre deve usar o Repositório Git do Cloud Manager, que fica vazio sem ramificações configuradas ou projetos de amostra. Para usar o Repositório Git do Cloud Manager, você receberá um **token de acesso privado** que permitirá usar qualquer cliente compatível com Git para criar ramificações, armazenar e recuperar seu código, listar o histórico de commit, etc.

Para obter mais informações sobre como configurar ramificações no Git, consulte [Configurar as ramificações de liberação](configure-your-release-branches.md).

Para obter mais informações sobre como usar o **Repositório Git** com o pipeline de CI/CD, consulte os documentos [Configurar pipeline de produção](configuring-production-pipelines.md) e [Configuração de pipeline de não produção](configuring-non-production-pipelines.md) para saber mais.

## Repositório local {#on-premise-repository}

Em alguns casos, você terá um Repositório Git existente e deseja continuar usando. Nesses casos, você pode usar o recurso suportado do Git para vários repositórios remotos. O desenvolvimento diário continuaria acontecendo no Repositório Git. Quando uma ramificação de versão estiver pronta para uma implantação em produção, você enviará seu código mais recente para o repositório Git do Cloud Manager e acionará o pipeline de CI/CD do Cloud Manager.

>[!NOTE]
>
>Para visualizar os comandos Git comuns, consulte o [Folha de características do Git](https://education.github.com/git-cheat-sheet-education.pdf).
