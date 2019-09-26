---
title: Compreensão dos conceitos antes de usar o Cloud Manager
seo-title: Compreensão dos conceitos antes de usar o Cloud Manager
description: 'null'
seo-description: 'null'
page-status-flag: nunca ativado
uuid: 55cc551a-e812-4102-96c8-13d2cdd79c84
contentOwner: jsyal
discoiquuid: c3fd3f4e-0b57-4377-b923-a440c74773d8
preview: verdadeiro
translation-type: tm+mt
source-git-commit: f135526c6a47f1502395e6d53f9e286c0f935da5

---


# Compreensão dos conceitos antes de usar o Cloud Manager{#understanding-concepts-before-using-cloud-manager}

Esta seção fornece conceitos e terminologias que devem ser conhecidos antes de trabalhar no Cloud Manager e aborda os seguintes tópicos:

* **Ambiente de implantação**
* **Repositório de código fonte**
* **Segurança e privacidade**
* **Visão geral do pipeline**
* **Recursos de ajuda**

## Ambiente de implantação {#deployment-environment}

Você pode ser novo no Adobe Experience Manager (AEM) 6.4 ou precisa de uma atualização para a versão AEM 6.4.

Se você for novo no AEM 6.4, já terá acesso ao Cloud Manager.

Se você já for um cliente, será necessário atualizar para o AEM 6.4 para ter acesso ao Cloud Manager. Você pode começar a usar o Cloud Manager, depois de receber o URL e as credenciais dos engenheiros de sucesso do cliente (CSE).

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:19:24.147-0400

Section is redundant with the section in the Overview topic

 -->

## Repositório de código fonte {#source-code-repository}

**Vários servidores** Git: Em alguns casos, os clientes terão um repositório git existente e desejam continuar usando-o.

Nesses casos, você pode usar o suporte da git para vários repositórios remotos. O desenvolvimento cotidiano continuaria a ocorrer no repositório git. Quando uma implantação for desejada, basta enviar o código mais recente para o repositório git do Cloud Manager.

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:20:46.002-0400

Looks like we lost some content, compared to the previous version

 -->

## Segurança e privacidade {#security-and-privacy}

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-04-21T02:38:21.417-0400

Query for Brad B.

 -->

## Visão geral do pipeline {#pipeline-overview}

O Cloud Manager oferecerá suporte a um único pipeline por programa (definição acima) que lida com as implantações no palco e na produção. ****

O ramo git usado para implantações de estágio e produção é mestre.

>[!NOTE]
>
>É uma prática recomendada usar o master como uma ramificação git para o palco e a produção, mas você pode usar qualquer uma das ramificações ao configurar o pipeline.

O processo de pipeline único é ilustrado abaixo:

![](assets/screen_shot_2018-04-30at30318pm.png)

### Como entender o fluxo {#understanding-the-flow}

You can configure your pipeline from the  tile from Cloud Manager UI.[!UICONTROL Pipeline Settings]

Refer to Using Cloud Manager, for more information.[](hhttps://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html)

The Deployment Manager is responsible for setting up the pipeline, that is:

* assigning application branch
* assigning deployment environments
* defining test options

When doing so, you first select a branch from their git repository. Next, define the trigger that will start the pipeline.

Next, you can define the parameters controlling the production deployment.

Finally, you will be able to configure the performance test parameters.

>[!NOTE]
>
>To learn about configuring the behavior and preferences for your pipeline, see Configuring Pipeline section in Using Cloud Manager.****[](using-cloud-manager.md)

### Help Resources {#help-resources}

Contact Adobe Managed Services Customer Success Engineer for support.

### Próximas etapas {#the-next-steps}

Now you have better understanding of the Cloud Manager concepts.

To set up your project, environment, and the team (user and roles), refer to [Setting up General Configurations for Cloud Manager](setting-configurations-for-cloud-manager.md).
