---
title: Adicionar usuários e funções
description: Saiba como usar o Admin Console para adicionar usuários e funções e criar perfis.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: dd96d773ea3e6b9c45886fe41b28d3dd70cb8a61
workflow-type: ht
source-wordcount: '780'
ht-degree: 100%

---


# Adicionar usuários e funções {#add-users-and-roles}

Vários recursos do [!UICONTROL Cloud Manager] exigem permissões específicas para serem usados. Por exemplo, somente certos usuários têm permissão para definir os KPIs (indicadores-chave de desempenho) para um programa. Essas permissões são logicamente agrupadas em funções.

Atualmente, o [!UICONTROL Cloud Manager] define quatro funções de usuário que controlam a disponibilidade de recursos específicos:

* Proprietário da empresa
* Gerenciador de programas
* Gerenciador de implantação
* Desenvolvedor

>[!NOTE]
>
>Para usar o [!UICONTROL Cloud Manager], você deve ter uma Adobe ID e um Contexto de produto do Adobe Managed Services.

## Definições de função {#role-definitions}

Essa tabela resume as funções.

| Função do [!UICONTROL Cloud Manager] | Descrição |
|--- |--- |
| Proprietário da empresa | Esse usuário é responsável por definir KPIs, aprovar implantações de produção e neutralizar falhas de nível 3 importantes, quando necessário. |
| Gerenciador de programas | Esse usuário usa o [!UICONTROL Cloud Manager] para executar a configuração da equipe, revisar o status, visualizar KPIs e, quando necessário, pode aprovar falhas de nível 3 importantes. |
| Gerenciador de implantação | Esse usuário gerencia operações de implantação e usa o [!UICONTROL Cloud Manager] para executar implantações de preparo/produção, editar os pipelines de CI/CD, aprovar falhas de nível 3 importantes quando necessário e acessar o repositório Git. |
| Desenvolvedor | Esse usuário desenvolve e testa o código de aplicativo personalizado e usa principalmente o [!UICONTROL Cloud Manager] para visualizar o status da implantação e acessar o repositório Git para confirmações de código. |
| Engenheiro de sucesso do cliente | Esse usuário geralmente oferece suporte ao sucesso de clientes do AMS e interage com o [!UICONTROL Cloud Manager] para executar implantações que exigem supervisão do CSE. |
| Autor de conteúdo | Esse usuário geralmente não interage com o [!UICONTROL Cloud Manager], mas pode usar o alternador de programa do [!UICONTROL Cloud Manager] para acessar o AEM. |

>[!NOTE]
>
>A persona de desenvolvedor no Admin Console não está relacionada à função de desenvolvedor do [!UICONTROL Cloud Manager].

## Uso do Admin Console para criar um perfil {#using-admin-console-to-create-a-profile}

As funções do [!UICONTROL Cloud Manager] são gerenciadas no Admin Console. Associações de função específicas são fornecidas adicionando o usuário a um perfil de produto do [!UICONTROL Cloud Manager].

O Admin Console é um local central para gerenciar seus direitos da Adobe em toda a organização. Para saber mais sobre o Adobe Admin Console, consulte a documentação do [Admin Console.](https://helpx.adobe.com/br/enterprise/using/admin-console.html)

Para fornecer as permissões de função apropriadas aos usuários do [!UICONTROL Cloud Manager], um administrador na organização do cliente deve criar novos perfis de produto no contexto do produto do [!UICONTROL AEM Managed Services] correspondente a cada uma das quatro funções do [!UICONTROL Cloud Manager]:

* Proprietário da empresa
* Gerenciador de implantação
* Desenvolvedor
* Gerenciador de programas

Você pode criar ou adicionar usuários/grupos a esses perfis de produtos com o Admin Console.

1. Faça logon no Admin Console em [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Clique na guia **Visão geral** e clique no produto que você deseja modificar no cartão **Produtos e serviços**. Se não estiver listado lá, use a guia **Produtos** para localizar o produto e clique nele.

   ![Guia de visão geral do Admin Console](/help/assets/admin-console-overview.png)

1. Na guia **Produtos**, clique no ambiente para o qual você deseja adicionar usuários/grupos aos perfis de produtos.

   ![Guia de produtos do Admin Console](/help/assets/admin-console-product.png)

1. Na guia **Perfil de produto** do produto, clique em **Novo perfil** para adicionar um novo perfil.

   ![Novo perfil](/help/assets/admin-console-product-profiles.png)

1. Forneça as informações para configurar uma nova função do [!UICONTROL Cloud Manager].

   * **Nome do perfil** - O **Nome do perfil** pode ser qualquer coisa. No entanto, para evitar confusão, é recomendável usar os valores da coluna **Nome de perfil recomendado**.
   * **Nome de exibição** - O **Nome de exibição** deve ser o valor técnico definido pelo [!UICONTROL Cloud Manager] (consulte a tabela a seguir).
   * **Grupo de permissões** - Você pode escolher um grupo de permissões para o perfil (nem sempre está disponível).

   ![Criação de um novo perfil](/help/assets/screen_shot_2018-05-04at171819.png)

   | Função | Nome de exibição (obrigatório) | Nome de perfil recomendado |
   |---|---|---|
   | Proprietário da empresa | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Função de proprietário da empresa |
   | Gerenciador de implantação | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Função do gerenciador de implantação |
   | Desenvolvedor | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Função do desenvolvedor |
   | Gerenciador de programas | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Função do gerenciador de programas |


1. Clique em **Concluído** para salvar o novo perfil.

## Atribuir perfis a usuários ou grupos de usuários {#assign-profiles}

Depois de criar perfis de produto, você pode atribuir usuários ou grupos de usuários a eles.

1. Faça logon no Admin Console em [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. No Admin Console, escolha a guia **Usuários**.

   ![Guia Usuários](/help/assets/admin-console-users.png)

1. Clique em **Usuários** no painel de navegação esquerdo e, em seguida, clique em um usuário para modificá-lo.

1. Clique no botão de reticências na seção **Produtos** e selecione **Editar**.

   ![Editar usuário](/help/assets/admin-console-edit-user.png)

1. Na caixa de diálogo **Editar produtos e grupos de usuários**, clique no botão de adição e selecione os perfis a serem atribuídos ao usuário.

   * Se o usuário já estiver atribuído às funções, o botão de adição será um botão de edição (um lápis), mas funcionará da mesma maneira.

   ![Editar produtos e grupos de usuários](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Clique em **Salvar** para salvar os perfis para o usuário.

Repita as mesmas etapas para atribuir perfis a grupos de usuários, mas selecione **Grupos de usuários** no painel de navegação esquerdo da guia **Usuários**. Clique em um grupo de usuários, selecione a guia **Perfis de produto atribuídos** e clique em **Atribuir perfil de produto** para atribuir perfis.

![Atribuir perfis ao grupo](/help/assets/admin-console-edit-user-groups.png)
