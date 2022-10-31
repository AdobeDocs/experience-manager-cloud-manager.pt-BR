---
title: Adicionar usuários e funções
description: Saiba como usar o Admin Console para adicionar usuários e funções e criar perfis.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: dd96d773ea3e6b9c45886fe41b28d3dd70cb8a61
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 22%

---


# Adicionar usuários e funções {#add-users-and-roles}

Vários recursos da [!UICONTROL Cloud Manager] requer permissões específicas para usar. Por exemplo, somente certos usuários têm permissão para definir os KPIs (indicadores-chave de desempenho) para um programa. Essas permissões são logicamente agrupadas em funções.

[!UICONTROL Cloud Manager] O atualmente define quatro funções para usuários que controlam a disponibilidade de recursos específicos:

* Proprietário da empresa
* Gerenciador de programas
* Gerenciador de implantação
* Desenvolvedor

>[!NOTE]
>
>Para usar [!UICONTROL Cloud Manager], você deve ter um Contexto de produto do Adobe ID e do Adobe Managed Services .

## Definições de função {#role-definitions}

Essa tabela resume as funções.

| [!UICONTROL Cloud Manager] Função | Descrição |
|--- |--- |
| Proprietário da empresa | Esse usuário é responsável por definir KPIs, aprovar implantações de produção e neutralizar falhas de nível 3 importantes, quando necessário. |
| Gerenciador de programas | Esse usuário usa [!UICONTROL Cloud Manager] para executar a configuração da equipe, revise o status, exiba KPIs e pode aprovar falhas importantes de três níveis quando necessário. |
| Gerenciador de implantação | Esse usuário gerencia operações e usos de implantação [!UICONTROL Cloud Manager] para executar implantações de armazenamento temporário/produção, edite os pipelines do CI/CD, aprove falhas importantes de 3 camadas quando necessário e possa acessar o repositório git. |
| Desenvolvedor | Esse usuário desenvolve e testa o código de aplicativo personalizado e usa principalmente [!UICONTROL Cloud Manager] para visualizar o status da implantação e acessar o repositório git para confirmações de código. |
| Engenheiro de sucesso do cliente | Esse usuário geralmente oferece suporte ao sucesso do cliente para clientes do AMS e interage com o [!UICONTROL Cloud Manager] para efeitos de execução de implantações que requerem supervisão da CSE. |
| Autor de conteúdo | Esse usuário geralmente não interage com [!UICONTROL Cloud Manager] mas pode usar o [!UICONTROL Cloud Manager] alternador de programas para acessar o AEM. |

>[!NOTE]
>
>A persona do Desenvolvedor no Admin Console não está relacionada à função do Desenvolvedor no [!UICONTROL Cloud Manager].

## Uso do Admin Console para criar um perfil {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] As funções são gerenciadas no Admin Console. Associações de função específicas são fornecidas adicionando o usuário a um [!UICONTROL Cloud Manager] perfil do produto.

O Admin Console é um local central para gerenciar seus direitos da Adobe em toda a organização. Para saber mais sobre o Adobe Admin Console, consulte a documentação do [Admin Console.](https://helpx.adobe.com/br/enterprise/using/admin-console.html)

Para fornecer as permissões com base em funções apropriadas ao [!UICONTROL Cloud Manager] , um administrador na organização do cliente deve criar novos perfis de produto no [!UICONTROL AEM Managed Services] contexto do produto correspondente a cada um dos quatro [!UICONTROL Cloud Manager] funções:

* Proprietário da empresa
* Gerenciador de implantação
* Desenvolvedor
* Gerenciador de programas

Você pode criar ou adicionar usuários/grupos a esses perfis de produtos com o Admin Console.

1. Faça logon no Admin Console em [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Clique no botão **Visão geral** , clique no produto que deseja modificar na guia **Produtos e serviços** cartão. Se não estiver listado lá, use a variável **Produtos** para localizar o produto e clique nele.

   ![Guia Visão geral do Admin Console](/help/assets/admin-console-overview.png)

1. No **Produtos** , clique no ambiente para o qual deseja adicionar usuários/grupos aos perfis de produtos.

   ![Guia de produtos do Admin Console](/help/assets/admin-console-product.png)

1. No **Perfil de produto** do produto, clique em **Novo perfil** para adicionar um novo perfil.

   ![Novo perfil](/help/assets/admin-console-product-profiles.png)

1. Forneça as informações para configurar uma nova função para [!UICONTROL Cloud Manager].

   * **Nome do perfil** - O **Nome do perfil** pode ser qualquer coisa, embora para evitar confusão, é recomendável usar os valores no **Nome de perfil recomendado** coluna.
   * **Nome de exibição** - O **Nome de exibição** deve ser o valor técnico definido por [!UICONTROL Cloud Manager] (ver quadro seguinte).
   * **Grupo de permissões** - Você pode escolher um grupo de permissões para o perfil (nem sempre disponível).

   ![Criação de um novo perfil](/help/assets/screen_shot_2018-05-04at171819.png)

   | Função | Nome de exibição (obrigatório) | Nome de perfil recomendado |
   |---|---|---|
   | Proprietário da empresa | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Função do proprietário da empresa |
   | Gerenciador de implantação | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Função do Gerenciador de Implantação |
   | Desenvolvedor | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Papel do desenvolvedor |
   | Gerenciador de programas | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Função do gerente do programa |


1. Clique em **Concluído** para salvar o novo perfil.

## Atribuir perfis a usuários ou grupos de usuários {#assign-profiles}

Depois de criar perfis de produto, você pode atribuir usuários ou grupos de usuários a eles.

1. Faça logon no Admin Console em [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. No Admin Console, escolha a variável **Usuários** guia .

   ![Guia Usuários](/help/assets/admin-console-users.png)

1. Clique em **Usuários** no painel de navegação esquerdo e, em seguida, clique em um usuário para modificá-lo.

1. Clique no botão de reticências no **Produtos** e selecione **Editar**.

   ![Editar usuário](/help/assets/admin-console-edit-user.png)

1. No **Editar produtos e grupos de usuários** , clique no botão de adição e selecione os perfis a serem atribuídos ao usuário.

   * Se o usuário já estiver atribuído às funções, o botão de adição será um botão de edição (um lápis), mas funcionará da mesma maneira.

   ![Editar produtos e grupos de usuários](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Clique em **Salvar** para salvar os perfis no usuário.

Repita as mesmas etapas para atribuir perfis a grupos de usuários, mas selecione **Grupos de usuários** no painel de navegação esquerdo do **Usuários** guia . Clique em um grupo de usuários e selecione o **Perfis de produto atribuídos** e clique em **Atribuir perfil de produto** para atribuir perfis.

![Atribuir perfis ao grupo](/help/assets/admin-console-edit-user-groups.png)
