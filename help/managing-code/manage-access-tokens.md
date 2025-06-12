---
title: Gerenciar tokens de acesso no Cloud Manager
description: Saiba como visualizar, editar e excluir tokens de acesso usados para Trazer seu próprio Git no Cloud Manager no Adobe Managed Services.
badge: label="Beta privado" type="Positive" url="/help/release-notes/current.md#access-tokens"
exl-id: 873aad0b-d7c6-4bc3-a70d-bbfdc1e02193
source-git-commit: b2a14280e84bb934053968b0e93e33d30fb6086a
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 3%

---

# Gerenciar tokens de acesso para repositórios externos {#manage-access-tokens}

O Cloud Manager usa tokens de acesso para gerenciar repositórios hospedados em plataformas Git externas. Anteriormente, se um token expirasse, o repositório associado precisaria ser reintegrado para permanecer operacional.

Agora, o recurso **Gerenciar tokens de acesso** permite gerenciar tokens com mais eficiência. Você pode exibir, renomear ou remover tokens conectados a provedores Git externos compatíveis, incluindo GitHub Enterprise, GitLab, Bitbucket e Azure DevOps.

Consulte também [Adicionar repositórios externos no Cloud Manager](/help/managing-code/external-repositories.md).

>[!NOTE]
>
>Os recursos descritos neste artigo só estão disponíveis por meio do programa beta privado. Para obter mais detalhes e para se inscrever no beta privado, consulte [Gerenciar tokens de acesso](/help/release-notes/current.md#access-tokens).

## Exibir tokens de acesso {#view-access-tokens}

1. Faça logon no Cloud Manager, em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/), e selecione a organização apropriada.
1. No console **[Meus Programas](/help/getting-started/navigation.md#my-programs-console)**, selecione o programa cujo token de acesso do Bring Your Own Git você deseja gerenciar.
1. No menu lateral, em **Programa**, clique em ![Ícone de estrutura de tópicos de pastas](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositórios**.
1. Próximo ao canto superior direito da página, clique em **Gerenciar tokens de acesso**.

   O botão **Gerenciar tokens de acesso** só estará visível se o programa estiver usando o recurso Trazer seu próprio Git.

   ![Caixa de diálogo Gerenciar Tokens de Acesso listando um token que está ativo e um token que está inativo](/help/managing-code/assets/access-tokens-manage.png)

1. Na caixa de diálogo **Gerenciar Tokens de Acesso**:
   * Todos os tokens de acesso são listados.
   * Você pode **editar** qualquer token.
   * Você pode **excluir** somente os tokens que estão *não em uso*. Se um token estiver em uso, o botão ![Excluir ícone da estrutura de tópicos](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) será desabilitado.

## Editar um token de acesso {#edit-access-tokens}

1. Na caixa de diálogo **Gerenciar Tokens de Acesso**, à direita de um nome de token, clique em ![Ícone Editar](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).
1. Na caixa de diálogo **Editar Token de Acesso**, atualize o **Nome do Token** ou o valor do **Token de Acesso**, ou ambos.

   Se o **Token de acesso** estiver em uso no momento, uma notificação será exibida avisando que todos os repositórios associados são revalidados automaticamente após a atualização.

   ![Caixa de diálogo Editar Token de Acesso](/help/managing-code/assets/access-tokens-edit.png)

1. Se o token estiver em uso, uma notificação avisará que todos os repositórios associados são revalidados automaticamente.

1. Clique em **Atualizar** para salvar as alterações.

## Excluir um token de acesso {#delete-access-token}

1. Na caixa de diálogo **Gerenciar Tokens de Acesso**, à direita de um nome de token, clique em ![Ícone Excluir](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)

   O ícone está desabilitado (![Excluir ícone da estrutura de tópicos](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)) para tokens que estão em uso no momento.

1. Na caixa de diálogo **Excluir Token de Acesso**, clique em **Excluir** para remover o token permanentemente.
