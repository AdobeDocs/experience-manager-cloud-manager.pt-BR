---
title: Adicionar usuários e funções
seo-title: Adicionar usuários e funções
description: 'null'
seo-description: Você pode atribuir associações de função específicas adicionando o usuário a um Perfil de produto do Experience Cloud Manager no Admin Console. Siga esta seção para saber mais.
uuid: fa 204 c 28-83 df -48 bb -8360-e 158 f 080 dee 7
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requisitos
discoiquuid: 1 b 421993-22 c 3-4 de 0-ba 64-c 1080 d 07 ad 5 e
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Adicionar usuários e funções{#add-users-and-roles}

Muitos recursos exigem [!UICONTROL Cloud Manager] permissões específicas para operar. Por exemplo, somente determinados usuários podem definir os Indicadores-chave de desempenho (kpis) para um programa. Essas permissões são logicamente agrupadas em funções.

[!UICONTROL Cloud Manager] atualmente define quatro funções para usuários que regulam a disponibilidade de recursos específicos:

* Proprietário de negócios
* Gerenciador de Programas
* Gerenciador de implantação
* Desenvolvedor

>[!CAUTION]
>
>Para usar [!UICONTROL Cloud Manager], você deve ter uma Adobe ID e o Contexto do produto Adobe Managed Services.

## Definições de função {#role-definitions}

>[!NOTE]
>
>The Developer persona in Admin Console is unrelated to the Developer role in [!UICONTROL Cloud Manager].

A tabela a seguir resume as funções:

| [!UICONTROL Cloud Manager] Funções | Descrição |
|--- |--- |
| Proprietário de negócios | Responsável pela definição de kpis, aprovação de implantações de produção e substituição de falhas importantes de 3 níveis. |
| Gerenciador de Programas | Usa [!UICONTROL Cloud Manager] para executar configuração de equipe, verificar o status e exibir kpis. Pode aprovar falhas importantes de 3 níveis. |
| Gerenciador de implantação | Gerencia operações de implantação. Usa [!UICONTROL Cloud Manager] para executar implantações de estágio/produção. Pode editar CI/CD Pipeline. Pode aprovar falhas importantes de 3 níveis. Pode obter acesso ao repositório Git. Entre em contato com seu representante CSE/AMS para solicitar. |
| Desenvolvedor | Desenvolve e teste o código do aplicativo personalizado. Principalmente usa [!UICONTROL Cloud Manager] para exibir o status. Deve obter acesso ao repositório Git para confirmar o código. Entre em contato com seu representante CSE/AMS ao adicionar um usuário com essa função para conceder acesso ao repositório Git. |
| Engenheiro de sucesso do cliente | Geralmente suporta o sucesso do cliente para clientes do AMS. Interage com [!UICONTROL Cloud Manager] a finalidade de execução de implantações que exigem a supervisão CSE. |
| Autor de conteúdo | Geralmente não interage [!UICONTROL Cloud Manager]com. Pode usar [!UICONTROL Cloud Manager] o Alternador de programas (com a partir [!UICONTROL Experience Cloud]de) para acessar o AEM. |

>[!NOTE]
>
>O acesso ao repositório [!UICONTROL Cloud Manager] Git é gerenciado pelo CSE. Entre em contato com eles para adicionar e remover usuários.
>
>Se um usuário recém-adicionado exigir acesso ao repositório Git, será necessário entrar em contato com seu representante CSE/AMS para ter o acesso concedido. Essas funções não fornecem acesso automático ao repositório Git. Você pode ter apenas 3 usuários com acesso ao Git repositório.

## Uso do Console de administração para criar um perfil {#using-admin-console-to-create-a-profile}

As funções são gerenciadas [!UICONTROL Cloud Manager] no Adobe Admin Console. As associações de função específicas são fornecidas adicionando o usuário a um [!UICONTROL Cloud Manager] Perfil de produto no Console de administração.

Você pode atribuir associações de função específicas adicionando o usuário a um [!UICONTROL Cloud Manager]**Perfil** de produto no Adobe Admin Console, um local central para gerenciar seus direitos da Adobe em toda a organização. Para saber mais sobre o Adobe Admin Console, consulte a documentação do [Console de administração](https://helpx.adobe.com/enterprise/using/admin-console.html).

>[!NOTE]
>
>Para acesse o admin Console e configure sua equipe (usuários e funções), abra um navegador e visite [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Para fornecer permissões apropriadas com base em funções aos [!UICONTROL Cloud Manager] usuários, um administrador na **Organização do cliente**, deve criar novos Perfis de produto no contexto [!UICONTROL AEM Managed Services] do produto.

Para fornecer permissões apropriadas com base em funções aos [!UICONTROL Cloud Manager] usuários, como administrador, você deve criar quatro novos Perfis de produtos no contexto [!UICONTROL AEM Managed Services] do produto correspondente a cada uma das quatro [!UICONTROL Cloud Manager] funções:

* Proprietário de negócios
* Gerenciador de implantação
* Desenvolvedor
* Gerenciador de Programas

Você pode criar ou adicionar usuários/grupos a esses Perfis de produtos com o Console [de administração](https://adminconsole.adobe.com/) para [!UICONTROL Cloud Manager], como mostrado na figura abaixo:

1. Faça logon no Admin Console e clique **em Novo perfil** para adicionar um novo perfil.

   ![](assets/admin_console_roles-1.png)

1. Preencha os campos para [!UICONTROL Cloud Manager]configurar uma nova função.

   Digite **Nome do perfil**, **Nome de exibição** para criar um novo perfil. Além disso, você pode selecionar um **Grupo de permissões** para o perfil.

   Clique **em Concluído** para concluir a etapa de criação do perfil.

   >[!NOTE]
   >
   >Ao criar esses perfis de produto, o Nome **de exibição** deve ser o valor técnico definido por [!UICONTROL Cloud Manager] (consulte a tabela abaixo). O Nome **do perfil** pode ser qualquer coisa, embora para evitar confusão seja recomendado usar os valores na coluna Nome *do perfil* recomendado abaixo. Para fazer isso, ao criar o Perfil de produto, desmarque o **mesmo nome do perfil** e especifique o valor correspondente como Nome **de exibição**.

   | **Função** | **Nome de exibição (obrigatório)** | **Nome de perfil recomendado** |
   |---|---|---|
   | Proprietário de negócios | CM_ BUSINESS_ OWNER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Função do proprietário do negócio |
   | Gerenciador de implantação | CM_ DEPLOYMENT_ MANAGER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Função do gerenciador de implantação |
   | Desenvolvedor | CM_ DEVELOPER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Função do desenvolvedor |
   | Gerenciador de Programas | CM_ PROGRAM_ MANAGER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Função do Gerenciador de Programas |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. Depois de criar o perfil de produto, você pode adicionar usuários (ou grupos) a esses Perfis de produto.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

