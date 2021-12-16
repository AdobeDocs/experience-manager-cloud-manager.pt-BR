---
title: Integração do Git com o Adobe Cloud Manager
description: Uma série de vídeo que analisa a configuração e integração de um repositório Git gerenciado pelo cliente (no local) com o Adobe Cloud Manager.
seo-title: Git Integration with Adobe Cloud Manager
seo-description: A video series that walks through the set up and integration of a customer-managed (on-premise) git repository with Adobe Cloud Manager.
feature: Git Repositories
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 0bc3e775ef2432cdb8d3bd5470953c07c6628148
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 4%

---

# Integração do Git com o Adobe Cloud Manager

O Adobe Cloud Manager vem provisionado com um único repositório Git usado para implantar código usando os pipelines de CI/CD do Cloud Manager. Os clientes podem usar o repositório Git do Cloud Manager imediatamente. Os clientes também têm a opção de integrar um **gerenciado pelo cliente** repositório Git com o Cloud Manager.

## Visão geral da integração do Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Esta série de vídeos explora vários casos de uso quando se trata de integrar um repositório Git gerenciado pelo cliente ao Cloud Manager, incluindo:

* [Sincronização inicial](#initial-sync)
* [Estratégia básica de ramificação](#branching-strategy)
* [Desenvolvimento de ramificação de recursos](#feature-development)
* [Implantação de produção](#production-deployment)
* [Sincronização das tags de versão](#sync-tags)

Para obter uma visão geral completa, consulte o [Guia do usuário do Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=pt-BR) A série de vídeos assume um conhecimento básico do gerenciamento de git e do controle de origem. Consulte a [recursos adicionais abaixo](#additional-resources) para obter mais detalhes sobre git.

>[!NOTE]
>
> As etapas e convenções de nomenclatura descritas nesta série de vídeo representam algumas práticas recomendadas para trabalhar com um repositório Git gerenciado pelo cliente e o Cloud Manager. Espera-se que as convenções e os fluxos de trabalho descritos sejam adaptados a equipes de desenvolvimento individuais.

## Sincronização inicial {#initial-sync}

Primeiras etapas para sincronizar um repositório Git gerenciado pelo cliente com o repositório Git do Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Estratégia básica de ramificação {#branching-strategy}

Defina uma estratégia básica de ramificação para aproveitar os [Condutas de produção e de não produção.](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html)

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Desenvolvimento de ramificação de recursos {#feature-development}

Use uma ramificação de recursos para isolar alterações de código em um repositório Git gerenciado pelo cliente e sincronizar com o repositório Git do Cloud Manager, a fim de usar um pipeline de não produção para testes de qualidade e validação de código.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Implantação de produção {#production-deployment}

Prepare o código para uma versão de produção em um repositório Git gerenciado pelo cliente e sincronize com o repositório Git do Cloud Manager para implantar em ambientes de preparo e produção.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Sincronização das tags de versão {#sync-tags}

Sincronize tags de versão de um repositório Git do Cloud Manager em um repositório Git gerenciado pelo cliente para fornecer visibilidade sobre qual código foi implantado em ambientes de preparo e produção.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Recursos adicionais {#additional-resources}

* [Documentação do Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [Recursos do GitHub](https://try.github.io)
* [Atlassiano Git Tutorials](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Folha de características do Git](https://education.github.com/git-cheat-sheet-education.pdf)
