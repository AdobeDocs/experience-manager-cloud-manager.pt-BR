---
title: Notas de versão do Cloud Manager 2025.7.0
description: Saiba mais sobre o lançamento do Cloud Manager 2025.7.0 no Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: a1f023b8ecc6fcae97832c5f3fad6bb8ae79ced1
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 62%

---

# Notas de versão do Cloud Manager 2025.7.0 no Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Saiba mais sobre o lançamento do [!UICONTROL Cloud Manager] 2025.7.0 no Adobe Managed Services.

Consulte também as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] 2025.7.0 é sexta-feira, 10 de julho de 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

A próxima versão está planejada para sexta-feira, 7 de agosto de 2025.

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


## Programas do Alpha/Beta {#beta-program}

Participe dos programas alfa e beta da Cloud Manager para obter acesso exclusivo aos recursos futuros antes do lançamento geral.

As seguintes oportunidades estão disponíveis no momento:


### Traga seu próprio Git: agora com suporte para GitLab e Bitbucket {#gitlab-bitbucket}

O recurso **Traga seu próprio Git** (BYOG) foi expandido para incluir suporte para repositórios externos, como GitLab e Bitbucket. Esse novo suporte é uma adição ao suporte já existente para repositórios GitHub privados e empresariais. Ao adicionar esses novos repositórios, também é possível vinculá-los diretamente aos seus pipelines. Você pode hospedar esses repositórios em plataformas de nuvem pública ou em sua infraestrutura ou nuvem privada. Essa integração também elimina a necessidade de sincronização constante do código com o repositório da Adobe e oferece a capacidade de validar solicitações de pull antes de mesclá-las em uma ramificação principal.

Os pipelines que usam repositórios externos (exceto os hospedados pelo GitHub) e o **Acionador de implantação** definidos como **Sobre alterações do Git** agora são iniciados automaticamente.

Consulte [Adicionar repositórios externos no Cloud Manager](/help/managing-code/external-repositories.md).

![Caixa de diálogo Adicionar repositório](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Atualmente, as verificações de qualidade do código de solicitação de pull prontas para uso são exclusivas de repositórios hospedados no GitHub, mas uma atualização para estender essa funcionalidade a outros fornecedores Git está em andamento.

Se tiver interesse em testar esse novo recurso e compartilhar o seu feedback, envie um email para [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) do seu endereço de email associado à sua Adobe ID. Inclua qual plataforma Git deseja usar e se você está em uma estrutura de repositório privado/público ou empresarial.

#### Gerenciar tokens de acesso{#access-tokens}

Use **Gerenciar tokens de acesso** com BYOG para exibir, renomear e excluir tokens de acesso associados a repositórios externos do Bring Your Own Git, como GitHub Enterprise, GitLab, Bitbucket e Azure DevOps.

Consulte [Gerenciar Tokens de Acesso](/help/managing-code/manage-access-tokens.md).

Se tiver interesse em testar esse novo recurso e compartilhar o seu feedback, envie um email para [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) do seu endereço de email associado à sua Adobe ID. Inclua qual plataforma Git deseja usar e se você está em uma estrutura de repositório privado/público ou empresarial.


## Correções de erros {#bug-fixes}

Não há correções de erros significativas na versão de julho do Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
