---
title: Notas de versão do Cloud Manager 2026.3.0
description: Saiba mais sobre o lançamento do Cloud Manager 2026.3.0 no Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: ee49b0732fdb870c4f768764aa75b240fd101b59
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 7%

---

# Notas de versão do Cloud Manager 2026.3.0 no Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Saiba mais sobre o lançamento do [!UICONTROL Cloud Manager] 2026.3.0 no Adobe Managed Services.

Consulte também as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] 2026.3.0 é quinta-feira, 5 de março de 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

A próxima versão planejada é quinta-feira, 2 de abril de 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novidades {#what-is-new}

* **Suporte para extensibilidade da interface do usuário no AEM Experience Hub**
O suporte para Extensões de Interface do Usuário no [AEM Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) agora está habilitado, permitindo que os desenvolvedores estendam a interface com funcionalidades e widgets personalizados criados com o Adobe App Builder.

  Para saber mais, consulte [AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/).

* **Os pipelines de configuração agora oferecem suporte a segredos gerenciados**

  Agora os usuários podem adicionar e gerenciar segredos diretamente nos pipelines de configuração do Cloud Manager. Esses segredos substituem com segurança os valores na especificação de configuração do pipeline e oferecem suporte a implantações flexíveis e específicas do ambiente.

  ![Opção Exibir/Editar variáveis no menu suspenso de um pipeline selecionado](/help/release-notes/assets/view-edit-variables-option.png)
  *Opção Exibir/Editar variáveis no menu suspenso de um pipeline selecionado.*

  ![Caixa de diálogo Configuração de Variáveis &#x200B;](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Caixa de diálogo Configuração de Variáveis.*

* **Estabilidade, desempenho e confiabilidade aprimoradas**

  Esta versão do inclui atualizações de otimização e manutenção que melhoraram a estabilidade, o desempenho e a confiabilidade do Cloud Manager.


## Programas do Beta {#beta-program}

Participe dos programas Beta da Cloud Manager para obter acesso exclusivo aos recursos futuros antes do lançamento geral.

As seguintes oportunidades estão disponíveis no momento:

<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### Criações mais rápidas com cache de módulo {#quick-build-cm-pipelines}

Um novo modelo de build compila apenas os módulos alterados (em vez do repositório inteiro) usando o armazenamento em cache no nível do módulo para reduzir os tempos de compilação. Ela se aplica a pipelines de qualidade de código, pilha completa e somente estágio.

![Caixa de diálogo Editar Pipeline de Não Produção mostrando as duas opções de Estratégia de Compilação que são Compilação Completa e Compilação Inteligente](/help/release-notes/assets/non-production-pipeline-edit.png)
*Caixa de diálogo Editar Pipeline de Não Produção mostrando as duas opções de Estratégia de Compilação que são Compilação Completa e Compilação Inteligente.*

Na caixa de diálogo **Adicionar/Editar Pipeline**, na guia **Código Source**, uma nova seção **Estratégia de Compilação** permite escolher uma das seguintes opções de compilação:

* **Compilação Completa** — compila todos os módulos no repositório em cada execução.
* **Compilação Inteligente** — cria apenas módulos que foram alterados desde a última confirmação, o que reduz o tempo geral de compilação.

Você controla quais pipelines usam a **Compilação inteligente**. Durante a versão beta, essa opção aparece somente para os pipelines **Qualidade do Código** e **Implantação de Desenvolvimento**.

Interessado? Envie um email para [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) com sua ID organizacional e ID do programa da Adobe.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## Correções de erros {#bug-fixes}

Não há correções de erros significativas na versão de março de 2026 do Cloud Manager no AMS.

<!--
Known Issues {#known-issues}

* A 
-->
