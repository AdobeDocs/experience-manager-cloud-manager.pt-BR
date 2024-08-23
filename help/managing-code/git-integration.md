---
title: Integração do Git com o Adobe Cloud Manager
description: Esta série de vídeos aborda a configuração e a integração de um repositório Git gerenciado pelo cliente (no local) com o Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 14%

---


# Integração do Git com o Adobe Cloud Manager

O Adobe Cloud Manager vem provisionado com um único repositório Git usado para implantar código usando os pipelines de CI/CD do Cloud Manager. Você pode usar o repositório Git da Cloud Manager pronto para uso ou também tem a opção de integrar um repositório Git no local ou gerenciado pelo cliente com o Cloud Manager.

## Visão geral da integração do Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/) (3 minutos, 11 segundos)

Esta série de vídeos explora vários casos de uso relacionados à integração de um repositório Git gerenciado pelo cliente com o Cloud Manager.

* [Sincronização inicial](#initial-sync)
* [Estratégia básica de ramificação](#branching-strategy)
* [Desenvolvimento de ramificação de recursos](#feature-development)
* [Implantação em produção](#production-deployment)
* [Sincronização das tags de versão](#sync-tags)

Esta série de vídeos presume um conhecimento básico sobre Git e gerenciamento de controle de origem. Consulte os [recursos adicionais abaixo](#additional-resources) para obter mais detalhes sobre o Git.

As etapas e convenções de nomenclatura descritas nesta série de vídeos representam algumas práticas recomendadas para trabalhar com um repositório Git gerenciado pelo cliente e o Cloud Manager. Espera-se que as convenções e os fluxos de trabalho descritos sejam adaptados a equipes de desenvolvimento individuais.

Para obter uma visão geral completa do Cloud Manager, consulte [Introdução ao Cloud Manager](/help/introduction.md).

## Sincronização inicial {#initial-sync}

Primeiras etapas para sincronizar um repositório Git gerenciado pelo cliente com o repositório Git da Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12) (8 minutos)

## Estratégia básica de ramificação {#branching-strategy}

Defina uma estratégia básica de ramificação para aproveitar a [produção](/help/using/production-pipelines.md) e os [pipelines de não produção](/help/using/non-production-pipelines.md) da Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12) (3 minutos, 48 segundos)

## Desenvolvimento de ramificação de recursos {#feature-development}

Use uma ramificação de recursos para isolar alterações de código em um repositório Git gerenciado pelo cliente e sincronizar com o repositório Git da Cloud Manager para usar um pipeline de não produção para testes de qualidade e validação de código.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12) (9 minutos)

## Implantação de produção {#production-deployment}

Prepare o código para uma versão de produção em um repositório Git gerenciado pelo cliente e sincronize com o repositório Git da Cloud Manager para implantar em ambientes de preparo e produção.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12) (6 minutos, 6 segundos)

## Sincronização de tags de versão {#sync-tags}

Você pode sincronizar tags de versão de um repositório Git da Cloud Manager em um repositório Git gerenciado pelo cliente. Essa capacidade fornece visibilidade sobre qual código foi implantado nos ambientes de preparo e produção.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12) (2 minutos, 57 segundos)

## Recursos adicionais {#additional-resources}

* [Introdução ao Cloud Manager](/help/introduction.md)
* [Recursos do GitHub](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Tutoriais sobre Git da Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Folha de referências do Git](https://education.github.com/git-cheat-sheet-education.pdf)
