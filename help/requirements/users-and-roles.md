---
title: Adicionar usuários e funções
description: Saiba como usar o Admin Console para adicionar usuários e funções e criar perfis.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: ht
source-wordcount: '536'
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
>Para usar o [!UICONTROL Cloud Manager], você deve ter uma Adobe ID e um contexto de produto do Adobe Managed Services.

## Definições de função {#role-definitions}

Essa tabela resume as funções.

| Função do [!UICONTROL Cloud Manager] | Descrição |
|--- |--- |
| Proprietário da empresa | Esse usuário é responsável por definir KPIs, aprovar implantações de produção e neutralizar falhas de nível 3 importantes, quando necessário. |
| Gerenciador de programas | Esse usuário usa o [!UICONTROL Cloud Manager] para executar a configuração da equipe, revisar o status, visualizar KPIs e pode aprovar falhas de nível 3 importantes, quando necessário. |
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

>[!NOTE]
>
>Para acessar o Admin Console e configurar sua equipe (usuários e funções), acesse [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

Para fornecer as permissões de função apropriadas aos usuários do [!UICONTROL Cloud Manager], um administrador na organização do cliente deve criar novos perfis de produto no contexto do produto do [!UICONTROL AEM Managed Services] correspondente a cada uma das quatro funções do [!UICONTROL Cloud Manager]:

* Proprietário da empresa
* Gerenciador de implantação
* Desenvolvedor
* Gerenciador de programas

Você pode criar ou adicionar usuários/grupos a esses perfis de produtos com o Admin Console.

1. Faça logon no Admin Console e clique em **Novo perfil** para adicionar um novo perfil.

   ![Novo perfil](/help/assets/admin_console_roles-1.png)

1. Forneça as informações para configurar uma nova função do [!UICONTROL Cloud Manager].

   * **Nome do perfil**
   * **Nome de exibição**
   * **Grupo de permissões**

1. Clique em **Concluído** para finalizar a etapa de criação do perfil.

Ao criar esses perfis de produto, o **Nome de exibição** deve ser o valor técnico definido pelo [!UICONTROL Cloud Manager] (consulte a tabela abaixo). O **Nome do perfil** pode ser qualquer coisa. No entanto, para evitar confusão, é recomendável usar os valores da coluna **Nome de perfil recomendado**. Para fazer isso, ao criar o Perfil do produto, desmarque a opção **Igual ao nome do perfil** e especifique o valor correspondente ao **Nome de exibição**.

| **Função** | **Nome de exibição (obrigatório)** | **Nome de perfil recomendado** |
|---|---|---|
| Proprietário da empresa | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Função do proprietário da empresa |
| Gerenciador de implantação | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Função de gerente de implantação |
| Desenvolvedor | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Função de desenvolvedor |
| Gerenciador de programas | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Função de gerente do programa |

![Criação de um novo perfil](/help/assets/screen_shot_2018-05-04at171819.png)

Depois de criar o perfil de produto, você pode adicionar usuários (ou grupos) a esses perfis de produto.

![Editar usuário](/help/assets/image2018-4-9_15-19-26.png)

![Grupos de usuários](/help/assets/image2018-4-9_15-16-47.png)
