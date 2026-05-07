---
title: Notas de versão do Cloud Manager 2026.5.0
description: Saiba mais sobre o lançamento do Cloud Manager 2026.5.0 no Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 0c2a9a946df6d5e1b0e4d5edb2715d8db98e9974
workflow-type: tm+mt
source-wordcount: 512
ht-degree: 6%

---


# Notas de versão do Cloud Manager 2026.5.0 no Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Saiba mais sobre a versão do [!UICONTROL Cloud Manager] 2026.5.0 no Adobe Managed Services.

Consulte também as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] 2026.5.0 é quinta-feira, 7 de maio de 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

A próxima versão planejada é quinta-feira, 4 de junho de 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novidades {#what-is-new}

Não há novos recursos significativos na versão de maio de 2026 do Cloud Manager no AMS.

## Programas do Beta {#beta-program}

Participe dos programas beta da Cloud Manager para obter acesso exclusivo aos recursos futuros antes do lançamento geral.

>[!IMPORTANT]
>
>As versões do Beta podem conter defeitos e são fornecidas &quot;NO ESTADO EM QUE SE ENCONTRAM&quot; sem garantias de nenhum tipo. A Adobe não tem nenhuma obrigação de manter, corrigir, atualizar, alterar, modificar ou oferecer suporte (por meio dos Serviços de suporte da Adobe ou de outra forma) às versões beta. A Adobe recomenda que os clientes tenham cuidado e não dependam do funcionamento ou do desempenho correto das versões beta, nem de qualquer documentação ou material que as acompanhe. Os recursos e as APIs na versão beta estão sujeitos a alterações sem aviso prévio. Portanto, qualquer uso das versões beta é de inteira responsabilidade do cliente.

As seguintes oportunidades do programa beta estão disponíveis no momento:

### Pipelines no nível da Web para o AEM Managed Services {#web-tier-pipelines}

O Cloud Manager agora oferece suporte a Pipelines de camada da Web dedicados para programas AMS, permitindo que as equipes implantem configurações de nível da Dispatcher e da Web independentemente de implantações de pilha completa. Isso permite uma iteração mais rápida em alterações no nível da Web, ao mesmo tempo que reduz execuções desnecessárias de pipeline completo. Quando um Pipeline no nível da Web é configurado, os pipelines de pilha completa ignoram automaticamente a implantação no nível da Web desse ambiente para evitar conflitos de implantação. A remoção do Pipeline no nível da Web restaura o comportamento de implantação padrão automaticamente.

Para participar da Beta, entre em contato com o engenheiro de sucesso do cliente da Adobe para saber mais.

### Criações mais rápidas com cache de módulo {#quick-build-cm-pipelines}

Um novo modelo de build compila apenas os módulos alterados (em vez do repositório inteiro) usando o armazenamento em cache no nível do módulo para reduzir os tempos de compilação. Ela se aplica aos pipelines de Qualidade de código e Pilha completa.

![Caixa de diálogo Editar Pipeline de Não Produção mostrando as duas opções de Estratégia de Compilação que são Compilação Completa e Compilação Inteligente](/help/release-notes/assets/non-production-pipeline-edit.png)
*Caixa de diálogo Editar Pipeline de Não Produção mostrando as duas opções de Estratégia de Compilação que são Compilação Completa e Compilação Inteligente.*

Na caixa de diálogo **Adicionar/Editar Pipeline**, na guia **Código Source**, uma nova seção **Estratégia de Compilação** permite escolher uma das seguintes opções de compilação:

* **Compilação Completa** — compila todos os módulos no repositório em cada execução.
* **Compilação Inteligente** — cria apenas módulos que foram alterados desde a última confirmação, o que reduz o tempo geral de compilação.

Consulte [Adicionar um pipeline de não produção](/help/using/non-production-pipelines.md#add-non-production-pipeline) e [Sobre o uso do Smart Build em um pipeline de não produção](/help/using/non-production-pipelines.md#about-smart-build).

Você controla quais pipelines usam a **Compilação Inteligente**. Durante a versão beta, essa opção aparece somente para os pipelines **Qualidade do código** e **Implantação do código de pilha completa de desenvolvimento**.

Para ingressar na Beta, envie um email para [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) com sua ID da organização da Adobe e a ID do programa.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## Correções de erros {#bug-fixes}

Não há correções de erros significativas na versão de maio de 2026 do Cloud Manager no AMS.

<!--
Known Issues {#known-issues}

* A 
-->
