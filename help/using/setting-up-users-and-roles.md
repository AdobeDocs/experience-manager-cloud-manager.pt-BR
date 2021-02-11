---
title: Adicionar usuários e funções
seo-title: Adicionar usuários e funções
description: Saiba mais sobre usuários e funções e como usar o Admin Console para criar um perfil
seo-description: É possível atribuir associações de função específicas adicionando o usuário a um Perfil de Produto do Cloud Manager no Admin Console. Siga esta seção para saber mais.
uuid: fa204c28-83df-48bb-8360-e158f080dee7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: 1b421993-22c3-4de0-ba64-c1080d07ad5e
translation-type: tm+mt
source-git-commit: 2dda85baa5e7ed9bfd8933df3580ec6fc3c210fd
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 32%

---


# Adicionar usuários e funções {#add-users-and-roles}

Muitos recursos em [!UICONTROL Cloud Manager] exigem permissões específicas para operar. Por exemplo, somente alguns usuários podem definir os Indicadores-chave de desempenho (KPIs) para um programa. Essas permissões são logicamente agrupadas em funções.

[!UICONTROL Cloud Manager] define atualmente quatro funções para usuários que controlam a disponibilidade de recursos específicos:

* Proprietário da empresa
* Gerenciador de programas
* Gerenciador de implantação
* Desenvolvedor

>[!CAUTION]
>
>Para usar [!UICONTROL Cloud Manager], você deve ter um Contexto de produto Adobe ID e o do Adobe Managed Services.

## Definições de função {#role-definitions}

>[!NOTE]
>
>A função Desenvolvedor no Admin Console não está relacionada à função Desenvolvedor em [!UICONTROL Cloud Manager].

A tabela a seguir resume as funções:

| [!UICONTROL Cloud Manager] Funções | Descrição |
|--- |--- |
| Proprietário da empresa | Responsável por definir KPIs, aprovar implantações de produção e substituir falhas importantes de 3 níveis. |
| Gerenciador de programas | Usa [!UICONTROL Cloud Manager] para executar a configuração do grupo, verificar o status e KPIs de visualização. Pode aprovar falhas importantes de 3 níveis. |
| Gerenciador de implantação | Gerencia operações de implantação. Usa [!UICONTROL Cloud Manager] para executar implantações de estágio/produção. É possível editar Pipelines de CI/CD. Pode aprovar falhas importantes de 3 níveis. Pode obter acesso ao repositório Git. |
| Desenvolvedor | Desenvolve e testa o código personalizado do aplicativo. Usa [!UICONTROL Cloud Manager] principalmente para status de visualização. Pode obter acesso ao repositório Git para confirmação de código. |
| Engenheiro de sucesso do cliente | Geralmente oferece suporte ao sucesso do cliente para clientes AMS. Interage com [!UICONTROL Cloud Manager] para fins de execução de implantações que exigem a supervisão CSE. |
| Autor de conteúdo | Geralmente, não interage com [!UICONTROL Cloud Manager]. Pode usar [!UICONTROL Cloud Manager] Comutador de Programas (navegando de [!UICONTROL Experience Cloud]) para acessar AEM. |

## Usando o Admin Console para criar um Perfil {#using-admin-console-to-create-a-profile}

As funções são gerenciadas para [!UICONTROL Cloud Manager] da Adobe Admin Console. Associações de função específicas são fornecidas adicionando o usuário a um [!UICONTROL Cloud Manager] Perfil de produto no Admin Console.

Atribua associações de função específicas ao adicionar o usuário a um [!UICONTROL Cloud Manager]Perfil de produto **do** no Adobe Admin Console, um local central para gerenciar seus direitos da Adobe em toda a organização. Para saber mais sobre o Adobe Admin Console, consulte a documentação do [Admin Console](https://helpx.adobe.com/br/enterprise/using/admin-console.html).

>[!NOTE]
>
>Para acessar o Admin Console e configurar sua equipe (usuários e funções), abra um navegador e visite [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Para fornecer as permissões com base em funções apropriadas aos usuários do [!UICONTROL Cloud Manager], um administrador na **organização** do cliente deve criar novos Perfis de produto no Contexto de produto dos [!UICONTROL AEM Managed Services].

Para fornecer as permissões apropriadas baseadas em funções aos usuários [!UICONTROL Cloud Manager], como administrador, você deve criar quatro novos Perfis de Produto no [!UICONTROL AEM Managed Services] Contexto de Produto correspondente a cada uma das quatro funções [!UICONTROL Cloud Manager]:

* Proprietário da empresa
* Gerenciador de implantação
* Desenvolvedor
* Gerenciador de programas

Você pode criar ou adicionar usuários/grupos a esses Perfis de Produto com o [Admin Console](https://adminconsole.adobe.com/) para [!UICONTROL Cloud Manager], conforme mostrado na figura abaixo:

1. Faça logon no Admin Console e clique em **Novo Perfil** para adicionar um novo perfil.

   ![](assets/admin_console_roles-1.png)

1. Preencha os campos para configurar uma nova função para [!UICONTROL Cloud Manager].

   Insira **Nome do perfil**, **Nome de exibição** para criar um novo perfil. Além disso, selecione um **Grupo de permissões** para o perfil.

   Clique em **Done** para concluir a etapa de criação do perfil.

   >[!NOTE]
   >
   >Ao criar esses perfis de produto, o **Nome de exibição** deve ser o valor técnico definido pelo [!UICONTROL Cloud Manager] (consulte a tabela abaixo). O **Nome do perfil** pode ser qualquer coisa. No entanto, para evitar confusão, é recomendável usar os valores na coluna *Nome de perfil recomendado* abaixo. Para fazer isso, ao criar o Perfil do produto, desmarque a opção **Igual ao nome do perfil** e especifique o valor correspondente ao **Nome de exibição**.

   | **Função** | **Nome de exibição (obrigatório)** | **Nome do Perfil recomendado** |
   |---|---|---|
   | Proprietário da empresa | CM_BUSINESS_OWNER_ROLE_PERFIL | [!UICONTROL Cloud Manager] - Função do proprietário da empresa |
   | Gerenciador de implantação | CM_DEPLOYMENT_MANAGER_ROLE_PERFIL | [!UICONTROL Cloud Manager] - Função do Gerenciador de implantação |
   | Desenvolvedor | CM_DEVELOPER_ROLE_PERFIL | [!UICONTROL Cloud Manager] - Função do desenvolvedor |
   | Gerenciador de programas | CM_PROGRAMA_MANAGER_ROLE_PERFIL | [!UICONTROL Cloud Manager] - Função do gerente do Programa |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. Depois de criar o perfil de produto, você pode adicionar usuários (ou grupos) a esses Perfis de produto.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

