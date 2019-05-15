---
title: Repositório de código-fonte
seo-title: Repositório de código-fonte para o Adobe AEM Cloud Manager
description: Siga esta página para saber mais sobre o repositório de git fornecido para cada programa que você possui no Cloud Manager.
seo-description: Siga esta página para saber mais sobre o repositório de git fornecido para cada programa que você possui no Adobe AEM Cloud Manager.
uuid: 2 c 42775 f -8703-43 f 7-bad 2-7 dc 086 ea 9 dd 7
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requisitos
discoiquuid: f 90 f 0 f 4 c-c 1 ff -47 f 6-8 d 97-ff 5018561 bf 2
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Repositório de código-fonte {#source-code-repository}

## Repositório do Gerenciador de nuvem {#cloud-manager-repository}

Sua [!UICONTROL AEM Managed Services] assinatura incluirá um repositório de código-fonte provisionado e gerenciado pela Adobe. O programa de cada cliente recebe um único e único **Repositório de Git**, onde seu código associado será armazenado e protegido.

Como prática recomendada, você deve sempre usar o Git Repository do Gerente da nuvem, que fica vazio sem qualquer ramificação configurada ou projetos de amostra. Para usar o Git Repository do Gerente da Nuvem, você receberá um token de acesso **privado** que permitirá que você use qualquer cliente compatível com Git para criar ramificações, armazenar e recuperar seu código, relacionar o histórico de confirmação etc.

Para obter mais informações sobre como configurar ramificações no Git, consulte [Configurar suas ramificações de lançamento](configure-your-release-branches.md).

For more information on how to use the Cloud Manager&#39;s **Git Repository** with the CI/CD Pipeline, see [Configuring your CI/CD pipeline](configuring-pipeline.md).

## Repositório local {#on-premise-repository}

Em alguns casos, você terá um Git Repository existente e deseja continuar usando. Nesses casos, você pode usar o recurso suportado Git para vários repositórios remotos. O desenvolvimento do dia para o dia continuaria a ocorrer no seu Git Repository. Quando uma ramificação de lançamento estiver pronta para uma implantação para produção, você enviará seu código mais recente para o repositório Git do Gerente da nuvem e acionará o pipeline CI/CD do Gerenciador de nuvem.

>[!NOTE]
>
>Para exibir os comandos comuns Git, consulte [o Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf).

