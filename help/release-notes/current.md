---
title: Notas de versão do Cloud Manager 2025.10.0
description: Saiba mais sobre o lançamento do Cloud Manager 2025.10.0 no Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: f62191a1b9dd67ea1e999e2db0bb05de66bf73f2
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 25%

---

# Notas de versão do Cloud Manager 2025.10.0 no Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Saiba mais sobre o lançamento do [!UICONTROL Cloud Manager] 2025.10.0 no Adobe Managed Services.

Consulte também as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] 2025.10.0 é sexta-feira, 2 de outubro de 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

A próxima versão está planejada para sexta-feira, 6 de novembro de 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novidades {#what-is-new}

Não há novos recursos significativos na versão de outubro do Cloud Manager.


## Programas do Beta {#beta-program}

Participe dos programas Beta da Cloud Manager para obter acesso exclusivo aos recursos futuros antes do lançamento geral.

As seguintes oportunidades estão disponíveis no momento:

### Extensibilidade e personalização do Experience Hub {#exp-hub-extensibility}

O [Experience Hub](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/experience-hub/experience-hub) serve como ponto de entrada para o AEM, personalizado para as necessidades da sua organização. Conte à Adobe sobre suas extensões existentes da interface do usuário do AEM para que elas possam ajudá-lo a ativá-las no Experience Hub com o mínimo de esforço.

![Diagrama do fluxo de trabalho de extensibilidade e personalização do Experience Hub](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Incorpore experiências personalizadas no Experience Hub para estender e personalizar o painel de sua organização. Além dos widgets integrados do Adobe, adicione os seus próprios usando a estrutura [Extensibilidade da interface](https://developer.adobe.com/uix/docs/). Crie aplicativos de interface do usuário com base no JavaScript e os mostre aos seus usuários para atender aos requisitos e fluxos de trabalho específicos da empresa.

Interessado no beta? Envie um email para [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) com sua Organização da Adobe e uma breve descrição da personalização que pretende criar.

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


### Traga seu próprio Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Os clientes agora podem integrar seus repositórios Git do Azure DevOps no Cloud Manager, com suporte para repositórios DevOps do Azure modernos e repositórios VSTS herdados (Visual Studio Team Services).

* Para usuários do Edge Delivery Services, o repositório integrado pode ser usado para sincronizar e implantar o código do site.
* Para usuários do AEM as a Cloud Service e do Adobe Managed Services (AMS), o repositório pode ser vinculado a pipelines de pilha completa e de front-end.

Em breve, haverá suporte para tipos adicionais de pipeline e validação de solicitação de pull por meio de pipelines de qualidade de código.

Consulte [Adicionar repositórios externos no Cloud Manager](/help/managing-code/external-repositories.md).

![Caixa de diálogo Adicionar repositório](/help/release-notes/assets/azure-repo.png)

Se tiver interesse em testar esse novo recurso e compartilhar o seu feedback, envie um email para [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) do seu endereço de email associado à sua Adobe ID. Inclua qual plataforma Git deseja usar e se você está em uma estrutura de repositório privado/público ou empresarial.

#### Gerenciar tokens de acesso{#manage-access-tokens}

Use **Gerenciar Tokens de Acesso** no Cloud Manager para exibir, renomear e excluir tokens de acesso associados a repositórios BYOG externos, como GitHub Enterprise, GitLab, Bitbucket e Azure DevOps.

Consulte [Gerenciar Tokens de Acesso](/help/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## Correções de erros {#bug-fixes}

Não há correções de bugs significativas na versão de outubro do Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
