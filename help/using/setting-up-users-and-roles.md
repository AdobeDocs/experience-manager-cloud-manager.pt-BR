---
title: Adicionar usuários e funções
seo-title: Adicionar usuários e funções
description: 'null'
seo-description: Você pode atribuir associações de função específicas adicionando o usuário a um Perfil de produto do Cloud Manager no Admin Console. Siga esta seção para saber mais.
uuid: fa204c28-83df-48bb-8360-e158f080dee7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requisitos
discoiquuid: 1b421993-22c3-4de0-ba64-c1080d07ad5e
translation-type: tm+mt
source-git-commit: 73203dca7b20570103af429cf933610941b787be

---


# Adicionar usuários e funções{#add-users-and-roles}

Muitos recursos em [!UICONTROL Cloud Manager] exigem permissões específicas para operar. Por exemplo, somente alguns usuários podem definir os Indicadores-chave de desempenho (KPIs) para um programa. Essas permissões são logicamente agrupadas em funções.

[!UICONTROL Cloud Manager] define atualmente quatro funções para usuários que controlam a disponibilidade de recursos específicos:

* Proprietário da empresa
* Gerente do programa
* Gerenciador de implantação
* Desenvolvedor

>[!CAUTION]
>
>Para usar [!UICONTROL Cloud Manager], você deve ter uma Adobe ID e o Contexto de produto do Adobe Managed Services.

## Definições de função {#role-definitions}

>[!NOTE]
>
>A função Desenvolvedor no Admin Console não está relacionada à função Desenvolvedor no [!UICONTROL Cloud Manager].

A tabela a seguir resume as funções:

| [!UICONTROL Cloud Manager] Funções | Descrição |
|--- |--- |
| Proprietário da empresa | Responsável por definir KPIs, aprovar implantações de produção e substituir falhas importantes de 3 níveis. |
| Gerente do programa | Usa [!UICONTROL Cloud Manager] para executar a configuração do grupo, verificar o status e exibir KPIs. Pode aprovar falhas importantes de 3 níveis. |
| Gerenciador de implantação | Gerencia operações de implantação. Usa [!UICONTROL Cloud Manager] para executar implantações de estágio/produção. É possível editar Pipelines de CI/CD. Pode aprovar falhas importantes de 3 níveis. Pode obter acesso ao repositório Git. Entre em contato com seu representante CSE/AMS para solicitar. |
| Desenvolvedor | Desenvolve e testa o código personalizado do aplicativo. Utiliza principalmente [!UICONTROL Cloud Manager] para ver o estado. Deve obter acesso ao repositório Git para confirmação de código. Entre em contato com seu representante CSE/AMS ao adicionar um usuário com essa função para conceder acesso ao repositório Git. |
| Engenheiro de sucesso do cliente | Geralmente oferece suporte ao sucesso do cliente para clientes AMS. Interage com [!UICONTROL Cloud Manager] a finalidade de executar implantações que exigem supervisão CSE. |
| Autor de conteúdo | Geralmente não interage com [!UICONTROL Cloud Manager]. Pode usar o [!UICONTROL Cloud Manager] Comutador de programas (navegando de [!UICONTROL Experience Cloud]) para acessar o AEM. |

>[!NOTE]
>
>O acesso ao repositório do [!UICONTROL Cloud Manager] Git é gerenciado pelo seu CSE. Entre em contato com eles para adicionar e remover usuários.
>
>Se um usuário recém-adicionado exigir acesso ao repositório Git, será necessário entrar em contato com seu representante CSE/AMS para que o acesso seja concedido. Essas funções não fornecem acesso automático ao repositório Git. Você só pode ter no máximo 3 usuários com acesso ao repositório Git.

## Usando o Admin Console para criar um perfil {#using-admin-console-to-create-a-profile}

As funções são gerenciadas [!UICONTROL Cloud Manager] pelo Adobe Admin Console. Associações de função específicas são fornecidas adicionando o usuário a um Perfil [!UICONTROL Cloud Manager] de produto no Admin Console.

Você pode atribuir associações de função específicas adicionando o usuário a um Perfil [!UICONTROL Cloud Manager] de **** produto no Adobe Admin Console, um local central para gerenciar seus direitos da Adobe em toda a organização. Para saber mais sobre o Adobe Admin Console, consulte a documentação do [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html).

>[!NOTE]
>
>Para acessar o Admin Console e configurar sua equipe (usuários e funções), abra um navegador e visite [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Para fornecer as permissões apropriadas baseadas em funções aos [!UICONTROL Cloud Manager] usuários, um administrador na **Organização** do cliente deve criar novos Perfis de produto no Contexto do [!UICONTROL AEM Managed Services] produto.

Para fornecer as permissões apropriadas com base em funções aos [!UICONTROL Cloud Manager] usuários, como administrador, você deve criar quatro novos Perfis de produto no Contexto [!UICONTROL AEM Managed Services] do produto, correspondentes a cada uma das quatro [!UICONTROL Cloud Manager] funções:

* Proprietário da empresa
* Gerenciador de implantação
* Desenvolvedor
* Gerente do programa

Você pode criar ou adicionar usuários/grupos a esses Perfis de produto com o Console [de](https://adminconsole.adobe.com/) administração para [!UICONTROL Cloud Manager], conforme mostrado na figura abaixo:

1. Faça logon no Admin Console e clique em **Novo perfil** para adicionar um novo perfil.

   ![](assets/admin_console_roles-1.png)

1. Preencha os campos para configurar uma nova função para [!UICONTROL Cloud Manager].

   Insira Nome **do** perfil, Nome **de** exibição para criar um novo perfil. Além disso, você pode selecionar um Grupo **de** permissões para o perfil.

   Clique em **Concluído** para concluir a etapa de criação do perfil.

   >[!NOTE]
   >
   >Ao criar esses perfis de produto, o Nome **de** exibição deve ser o valor técnico definido por [!UICONTROL Cloud Manager] (consulte a tabela abaixo). O Nome **do** perfil pode ser qualquer coisa, embora, para evitar confusão, é recomendável usar os valores na coluna Nome *do perfil* recomendado abaixo. Para fazer isso, ao criar o Perfil do produto, desmarque a opção **Igual ao Nome** do perfil e especifique o valor correspondente ao Nome **de** exibição.

   | **Função** | **Nome de exibição (obrigatório)** | **Nome de perfil recomendado** |
   |---|---|---|
   | Proprietário da empresa | CM_BUSINESS_OWNER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Função do proprietário da empresa |
   | Gerenciador de implantação | CM_DEPLOYMENT_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Função do Gerenciador de implantação |
   | Desenvolvedor | CM_DEVELOPER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Função do desenvolvedor |
   | Gerente do programa | CM_PROGRAM_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Função do gerente do programa |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. Depois de criar o perfil do produto, você pode adicionar usuários (ou grupos) a esses Perfis de produto.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

