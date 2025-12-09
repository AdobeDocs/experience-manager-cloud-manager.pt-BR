---
title: Integração do Git com o Adobe Cloud Manager
description: Esta série de vídeos aborda a configuração e a integração de um repositório Git gerenciado pelo cliente (no local) com o Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 75baacd1fd6f36ca1d6ea5c1993516569ab6ef47
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 99%

---


# Integração do Git com o Adobe Cloud Manager

O Adobe Cloud Manager vem provisionado com um único repositório Git que é usado para implantar código através de seus pipelines de CI/CD. É possível usar o repositório Git pronto para uso do Cloud Manager. Também há a opção de integrar um repositório Git no local ou gerenciado pelo cliente com o Cloud Manager.

## Visão geral da integração do Git

>[!VIDEO](https://video.tv.adobe.com/v/31192?captions=por_br)

Esta série de vídeos explora vários casos de uso relacionados à integração de um repositório Git gerenciado pelo cliente com o Cloud Manager.

* [Sincronização inicial](#initial-sync)
* [Estratégia básica de ramificação](#branching-strategy)
* [Desenvolvimento de ramificação de recursos](#feature-development)
* [Implantação em produção](#production-deployment)
* [Sincronização das tags de versão](#sync-tags)

Esta série de vídeos presume um conhecimento básico do gerenciamento do controle de origem e do Git. Consulte os [recursos adicionais abaixo](#additional-resources) para obter mais detalhes sobre o Git.

As etapas e convenções de nomenclatura descritas nesta série de vídeos representam algumas práticas recomendadas para trabalhar com um repositório Git gerenciado pelo cliente e com o Cloud Manager. Espera-se que as convenções e os fluxos de trabalho descritos sejam adaptados a equipes de desenvolvimento individuais.

Para ter uma visão geral completa do Cloud Manager, consulte a [Introdução ao Cloud Manager](/help/introduction.md).

## Sincronização inicial {#initial-sync}

Primeiras etapas para sincronizar um repositório Git gerenciado pelo cliente com o do Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/31191/?captions=por_br&quality=12)

## Estratégia básica de ramificação {#branching-strategy}

Defina uma estratégia básica de ramificação para aproveitar os [pipelines de produção](/help/using/production-pipelines.md) e de [não produção](/help/using/non-production-pipelines.md) do Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/31190/?captions=por_br&quality=12)

## Desenvolvimento de ramificação de recursos {#feature-development}

Use uma ramificação de recursos para isolar alterações de código em um repositório Git gerenciado pelo cliente e sincronizar com o repositório Git do Cloud Manager, a fim de usar um pipeline de não produção para testes de validação e qualidade de código.

>[!VIDEO](https://video.tv.adobe.com/v/31189/?captions=por_br&quality=12)

## Implantação de produção {#production-deployment}

Prepare o código para uma versão de produção em um repositório Git gerenciado pelo cliente e sincronize com o repositório Git do Cloud Manager para implantar em ambientes de preparo e produção.

>[!VIDEO](https://video.tv.adobe.com/v/31188/?captions=por_br&quality=12)

## Sincronizar tags de versão {#sync-tags}

Você pode sincronizar tags de versão de um repositório Git do Cloud Manager em um repositório Git gerenciado pelo cliente. Essa capacidade fornece visibilidade sobre qual código foi implantado nos ambientes de preparo e produção.

>[!VIDEO](https://video.tv.adobe.com/v/31187/?captions=por_br&quality=12)

## Recursos adicionais {#additional-resources}

* [Introdução ao Cloud Manager](/help/introduction.md)
* [Recursos do GitHub](https://docs.github.com/en/get-started/git-basics/set-up-git)
* [Tutoriais sobre Git da Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Folha de referências do Git](https://education.github.com/git-cheat-sheet-education.pdf)
