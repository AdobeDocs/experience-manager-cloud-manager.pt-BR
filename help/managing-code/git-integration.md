---
title: Integração do Git com o Adobe Cloud Manager
description: Esta série de vídeos aborda a configuração e a integração de um repositório Git gerenciado pelo cliente (no local) com o Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
TQID: https://experienceleague.adobe.com/fyGrLuc1bIBY9ZAgYiULxxJQy-ZZBLYtAAdYgqzSLAM
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2011f63c513689f571d21772752348388c2f342a
workflow-type: tm+mt
source-wordcount: 356
ht-degree: 76%

---

# Integração do Git com o Adobe Cloud Manager

O Adobe Cloud Manager vem provisionado com um único repositório Git que é usado para implantar código através de seus pipelines de CI/CD. Você pode usar o repositório Git da Cloud Manager conforme fornecido ou tem a opção de integrar um repositório Git local ou gerenciado pelo cliente ao Cloud Manager.

## Visão geral da integração do Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Esta série de vídeos explora vários casos de uso relacionados à integração de um repositório Git gerenciado pelo cliente com o Cloud Manager.

* [Sincronização inicial](#initial-sync)
* [Estratégia básica de ramificação](#branching-strategy)
* [Desenvolvimento de ramificação de recursos](#feature-development)
* [Implantação em produção](#production-deployment)
* [Sincronização das tags de versão](#sync-tags)

Esta série de vídeos requer conhecimento básico sobre Git e gerenciamento de controle de origem. Consulte os [recursos adicionais abaixo](#additional-resources) para obter mais detalhes sobre o Git.

As etapas e convenções de nomenclatura descritas nesta série de vídeos representam algumas práticas recomendadas para trabalhar com um repositório Git gerenciado pelo cliente e com o Cloud Manager. As convenções e os fluxos de trabalho descritos são adaptados para equipes de desenvolvimento individuais.

Para ter uma visão geral completa do Cloud Manager, consulte a [Introdução ao Cloud Manager](/help/introduction.md).

## Sincronização inicial {#initial-sync}

Primeiras etapas para sincronizar um repositório Git gerenciado pelo cliente com o do Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Estratégia básica de ramificação {#branching-strategy}

Configure uma estratégia básica de ramificação para usar os [pipelines de produção](/help/using/production-pipelines.md) e [não produção](/help/using/non-production-pipelines.md) da Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Desenvolvimento de ramificação de recursos {#feature-development}

Use uma ramificação de recursos para isolar alterações de código em um repositório Git gerenciado pelo cliente e sincronizar com o repositório Git do Cloud Manager, a fim de usar um pipeline de não produção para testes de validação e qualidade de código.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Implantação de produção {#production-deployment}

Prepare o código para uma versão de produção em um repositório Git gerenciado pelo cliente e sincronize com o repositório Git do Cloud Manager para implantar em ambientes de preparo e produção.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Sincronizar tags de versão {#sync-tags}

Você pode sincronizar tags de versão de um repositório Git do Cloud Manager em um repositório Git gerenciado pelo cliente. Essa capacidade fornece visibilidade sobre qual código foi implantado nos ambientes de preparo e produção.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Recursos adicionais {#additional-resources}

* [Introdução ao Cloud Manager](/help/introduction.md)
* [Recursos do GitHub](https://docs.github.com/en/get-started/git-basics/set-up-git)
* [Tutoriais Atlassian sobre o Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Folha de características do Git](https://education.github.com/git-cheat-sheet-education.pdf)
