---
title: Notas de versão do Cloud Manager 2025.8.0
description: Saiba mais sobre o lançamento do Cloud Manager 2025.8.0 no Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: a96bc45242ee6c6b06b4354756a67562150f385c
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 33%

---

# Notas de versão do Cloud Manager 2025.8.0 no Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Saiba mais sobre o lançamento do [!UICONTROL Cloud Manager] 2025.8.0 no Adobe Managed Services.

Consulte também as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] 2025.8.0 é sexta-feira, 7 de agosto de 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

A próxima versão está planejada para sexta-feira, 4 de setembro de 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Novidades {#what-is-new}



* **Pipelines somente de preparo e somente de produção**

  O Cloud Manager agora oferece suporte a pipelines somente de preparo e produção. Esse recurso permite dividir as implantações de produção de pilha completa em pipelines menores e específicos de propósito. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![Caixa de diálogo Adicionar pipeline de não produção com o botão de opção Código de pilha completa selecionado e ambiente de preparo selecionado](/help/release-notes/assets/add-non-production-pipeline.png)

  Consulte [Pipelines somente de preparo e somente de produção](/help/using/stage-prod-only.md).

* **Favoritos do pipeline**

  Nesta versão, o Cloud Manager apresenta a capacidade de fixar pipelines favoritos, permitindo que você marque pipelines específicos como favoritos para que eles apareçam no topo da lista na página **Pipelines**. Esse aprimoramento facilita a localização e a execução de pipelines acessados com frequência. <!-- CMGR-68293 -->

  ![Pipelines marcados como favoritos](/help/release-notes/assets/pipeline-favorites.png) *Dois pipelines marcados como favoritos.*

  Consulte [Marcar favoritos do pipeline](/help/using/managing-pipelines.md#pipeline-favorites).


## Programas do Beta {#beta-program}

Participe dos programas Beta da Cloud Manager para obter acesso exclusivo aos recursos futuros antes do lançamento geral.

As seguintes oportunidades estão disponíveis no momento:


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

Se você estiver interessado em testar este novo recurso e compartilhar seus comentários, envie um email para [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) com seu endereço de email associado à sua Adobe ID.

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->


## Correções de erros {#bug-fixes}

Não há correções de erros significativas na versão de julho do Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
