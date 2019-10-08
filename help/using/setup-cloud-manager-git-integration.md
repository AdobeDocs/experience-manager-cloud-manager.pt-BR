---
title: Integração do Git com o Adobe Cloud Manager
description: Uma série de vídeos que acompanha a configuração e a integração de um repositório git gerenciado pelo cliente (no local) com o Adobe Cloud Manager.
seo-title: Integração do Git com o Adobe Cloud Manager
seo-description: Uma série de vídeos que acompanha a configuração e a integração de um repositório git gerenciado pelo cliente (no local) com o Adobe Cloud Manager.
translation-type: tm+mt
source-git-commit: 519f43ff16e0474951f97798a8e070141e5c124b

---


# Integração do Git com o Adobe Cloud Manager

O Adobe Cloud Manager é fornecido com um único repositório git usado para implantar código usando os pipelines CI/CD do Cloud Manager. Os clientes podem usar o repositório git do Gerenciador de nuvem imediatamente. Os clientes também têm a opção de integrar um repositório git no local ou gerenciado pelo **cliente** com o Cloud Manager.

## Visão geral da integração do Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/?captions=por_br)

Esta série de vídeos explora vários casos de uso quando se trata de integrar um repositório git gerenciado pelo cliente ao Cloud Manager, incluindo:

* [Sincronização inicial](#initial-sync)
* [Estratégia básica de ramificação](#branching-strategy)
* [Desenvolvimento de Ramificação de Recursos](#feature-development)
* [Implantação de produção](#production-deployment)
* [Sincronizando tags de versão](#sync-tags)

Para obter uma visão geral completa, consulte o Guia [do usuário do](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)Cloud Manager. A série de vídeos assume um conhecimento básico sobre gerenciamento de git e controle de origem. Consulte os recursos [adicionais abaixo](#additional-resources) para obter mais detalhes sobre git.

>[!NOTE]
>
> As etapas e convenções de nomenclatura descritas nesta série de vídeo representam algumas práticas recomendadas para trabalhar com um repositório git gerenciado pelo cliente e o Cloud Manager. Espera-se que as convenções e os fluxos de trabalho descritos sejam adaptados a equipes de desenvolvimento individuais.

## Sincronização inicial {#initial-sync}

Primeiras etapas para sincronizar um repositório Git gerenciado pelo cliente com o repositório Git do Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12&captions=por_br)

## Estratégia básica de ramificação {#branching-strategy}

Configure uma estratégia básica de ramificação para aproveitar os pipelines de [produção e não produção do Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html).

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12&captions=por_br)

## Desenvolvimento de Ramificação de Recursos {#feature-development}

Use uma ramificação de recursos para isolar as alterações de código em um repositório git gerenciado pelo cliente e sincronizar com o repositório git do Cloud Manager para usar um pipeline de não produção para testes de qualidade de código e validação.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12&captions=por_br)

## Implantação de produção {#production-deployment}

Prepare o código para uma versão de produção em um repositório git gerenciado pelo cliente e sincronize com o repositório git do Cloud Manager para implantar em ambientes de estágio e produção.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12&captions=por_br)

## Sincronizando tags de versão {#sync-tags}

Sincronize as tags de versão de um repositório git do Cloud Manager em um repositório git gerenciado pelo cliente para fornecer visibilidade sobre qual código foi implantado nos ambientes de estágio e produção.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12&captions=por_br)

## Additional Resources {#additional-resources}

* [Documentação do Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [Recursos do GitHub](https://try.github.io)
* [Tutoriais do Git Atlassiano](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)