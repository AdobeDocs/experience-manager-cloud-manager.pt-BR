---
title: Notas de versão do Cloud Manager 2026.7.0
description: Saiba mais sobre o lançamento do Cloud Manager 2026.7.0 no Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: acd33650c938d49bac5c319f8c938202fe543bbd
workflow-type: tm+mt
source-wordcount: 391
ht-degree: 9%

---


# Notas de versão do Cloud Manager 2026.7.0 no Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Saiba mais sobre a versão do [!UICONTROL Cloud Manager] 2026.6.0 no Adobe Managed Services.

Consulte também as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] 2026.7.0 é quinta-feira, 9 de julho de 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

A próxima versão planejada é quinta-feira, 6 de agosto de 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novidades {#what-is-new}

<!-- There are no significant new features in the June 2026 Cloud Manager on AMS release. -->

* **Desempenho de compilação aprimorado com cache de módulo**
Um novo modelo de build compila apenas módulos alterados (em vez do repositório inteiro) usando o armazenamento em cache no nível do módulo para melhorar o desempenho da build. Aplica-se a pipelines de produção. Você controla quais pipelines de produção usam o **Smart Build**.

  Para obter mais informações, consulte o seguinte:

   * [Sobre o uso da Compilação Inteligente em um pipeline de produção](/help/using/production-pipelines.md#about-smart-build) e [Sobre o uso da Compilação Inteligente em um pipeline de não produção](/help/using/non-production-pipelines.md#about-smart-build)
   * [Adicionar um pipeline de produção](/help/using/production-pipelines.md##adding-production-pipeline) e [Adicionar um pipeline de não produção](/help/using/non-production-pipelines.md#add-non-production-pipeline).

## Programas do Beta {#beta-program}

Participe dos programas beta da Cloud Manager para obter acesso exclusivo aos recursos futuros antes do lançamento geral.

>[!IMPORTANT]
>
>As versões do Beta contêm defeitos e são fornecidas &quot;NO ESTADO EM QUE SE ENCONTRAM&quot; sem garantias de nenhum tipo. A Adobe não tem nenhuma obrigação de manter, corrigir, atualizar, alterar, modificar ou oferecer suporte (por meio dos Serviços de suporte da Adobe ou de outra forma) às versões beta. Os clientes usam versões beta por sua conta e risco e não devem depender do funcionamento ou do desempenho corretos das versões beta, nem de qualquer documentação ou material que as acompanhe. Os recursos e as APIs na versão beta estão sujeitos a alterações sem aviso prévio. Qualquer uso das versões beta é totalmente de responsabilidade do cliente.

As seguintes oportunidades do programa beta estão disponíveis no momento:

### Pipelines no nível da Web para o AEM Managed Services {#web-tier-pipelines}

O Cloud Manager agora oferece suporte a Pipelines de camada da Web dedicados para programas AMS, permitindo que as equipes implantem configurações de nível da Dispatcher e da Web independentemente de implantações de pilha completa. Isso permite uma iteração mais rápida em alterações no nível da Web, ao mesmo tempo que reduz execuções desnecessárias de pipeline completo. Quando um Pipeline no nível da Web é configurado, os pipelines de pilha completa ignoram automaticamente a implantação no nível da Web desse ambiente para evitar conflitos de implantação. A remoção do Pipeline no nível da Web restaura o comportamento de implantação padrão automaticamente.

Para participar da Beta, entre em contato com o engenheiro de sucesso do cliente da Adobe para saber mais.




## Correções de erros {#bug-fixes}

Não há correções de erros significativas na versão de julho de 2026 do Cloud Manager no AMS.

<!--
Known Issues {#known-issues}

* A 
-->
