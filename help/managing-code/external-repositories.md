---
title: Adicionar repositórios externos no Cloud Manager - Adoção antecipada
description: Saiba como adicionar um repositório externo no Cloud Manager. O Cloud Manager oferece suporte à integração com repositórios GitHub, GitLab e Bitbucket.
exl-id: 4500cacc-5e27-4bbb-b8f6-5144dac7e6da
source-git-commit: 58cdebf819f2737be5d8e129ff5b9783888f3c21
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 98%

---

# Adicionar repositórios externos no Cloud Manager {#external-repositories}

Saiba como adicionar um repositório externo no Cloud Manager. O Cloud Manager oferece suporte à integração com repositórios GitHub, GitLab e Bitbucket.

>[!NOTE]
>
>Este recurso só está disponível por meio do [programa de adoção antecipada](/help/release-notes/current.md#early-adoption).

## Configurar um repositório externo

A configuração de um repositório externo no Cloud Manager consiste em três etapas:

1. [Adicionar um repositório externo](#add-external-repo) a um programa selecionado.
1. Forneça um token de acesso ao repositório externo.
1. Valide a propriedade do repositório externo.


## Adicione um repositório externo {#add-ext-repo}

1. Faça logon no Cloud Manager, em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/), e selecione a organização apropriada.

1. No console **[Meus programas](/help/getting-started/navigation.md#my-programs-console), selecione o programa ao qual deseja vincular um repositório externo.


1. No menu lateral, em **Serviços**, selecione ![Ícone de pasta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositórios**.

   ![A página Repositórios](/help/managing-code/assets/repositories-tab.png)

1. Próximo ao canto superior direito da página **Repositórios**, clique em **Adicionar Repositório**.

1. Na caixa de diálogo **Adicionar repositório**, selecione **Repositório privado** para vincular um repositório Git externo ao seu programa.

   ![Adicionar repositório próprio](/help/managing-code/assets/repositories-private-repo-type.png)

1. Em cada campo respectivo, forneça os seguintes detalhes sobre o repositório:

   | Texto | Descrição |
   | --- | --- |
   | **Nome do repositório** | Obrigatório. Um nome expressivo para o novo repositório. |
   | **URL do repositório** | Obrigatório. O URL do repositório.<br><br> Se você estiver usando um repositório hospedado pelo GitHub, o caminho deverá terminar em `.git`.<br>Por exemplo, *`https://github.com/org-name/repo-name.git`* (o caminho do URL é apenas para fins ilustrativos).<br><br>Se você estiver usando um repositório externo, ele deverá usar o seguinte formato de caminho de URL:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> ou<br>`https://self-hosted-domain/org-name/repo-name.git`<br>e corresponder ao seu fornecedor de Git. |
   | **Selecionar tipo de repositório** | Obrigatório. Selecione o tipo de repositório que você está usando: **GitHub**, **GitLab** ou **BitBucket**. Se o caminho do URL do repositório acima incluir o nome do fornecedor do Git, como GitLab ou Bitbucket, o tipo de repositório já estará pré-selecionado. |
   | **Descrição** | Opcional. Uma descrição detalhada do repositório. |

1. Clique em **Salvar** para adicionar o repositório.

1. Na caixa de diálogo **Validação de propriedade de repositório privado**, forneça um token de acesso para validar a propriedade do repositório externo para que você possa acessá-lo.

   ![Seleção de um token de acesso para um repositório](/help/managing-code/assets/repositories-exisiting-access-token.png)
   *Seleção de um token de acesso para um repositório BitBucket.*

   | Tipo de token | Descrição |
   | --- | --- |
   | **Usar token de acesso já existente** | Se você já forneceu um token de acesso ao repositório para sua organização e tem acesso a vários repositórios, você pode selecionar um token. Use a lista suspensa **Nome do token** para escolher o token que deseja aplicar ao repositório. Caso contrário, adicione um novo token de acesso. |
   | **Adicionar novo token de acesso** | **Tipo de repositório: GitHub**<br>• No campo de texto **Nome do token**, digite um nome para o token de acesso que você está criando.<br>• Crie um token de acesso pessoal seguindo as instruções na [documentação do GitHub](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).<br>• Permissões necessárias:<br>  • `Read access to metadata`.<br>  • `Read and write access to code and pull requests`.<br>• No campo **Token de acesso**, cole o token que você acabou de criar. |
   |  | **Tipo de repositório: GitLab**<br>• No campo de texto **Nome do token**, digite um nome para o token de acesso que você está criando.<br>• Crie um token de acesso pessoal seguindo as instruções na [documentação do GitLab](https://docs.gitlab.com/user/profile/personal_access_tokens/).<br>• Permissões necessárias:<br>  • `api`<br>  • `read_api`<br>  • `read_repository`<br>  • `write_repository`<br>• No campo **Token de acesso**, cole o token que você acabou de criar. |
   |  | **Tipo de repositório: Bitbucket**<br>• No campo de texto **Nome do token**, digite um nome para o token de acesso que você está criando.<br>• Crie um token de acesso ao repositório usando a [documentação do Bitbucket](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<br>• Permissões necessárias:<br>  • `Read and write access to code and pull requests`. |

   >[!NOTE]
   >
   >O recurso **Adicionar novo token de acesso** está atualmente na fase de Adoção antecipada. Funcionalidades adicionais estão sendo planejadas. Como resultado, as permissões necessárias para tokens de acesso podem mudar. Além disso, a interface de usuário para gerenciamento de tokens pode ser atualizada, possivelmente incluindo recursos como datas de expiração de tokens. E verificações automatizadas para garantir que os tokens vinculados aos repositórios permaneçam válidos.

1. Clique em **Validar**.

Após a validação, o repositório externo estará pronto para ser usado e vinculado a um pipeline.

## Vincular um repositório externo validado a um pipeline {#validate-ext-repo}

1. Adicionar ou editar um pipeline:
   * [Adicionar um pipeline de produção](/help/using/production-pipelines.md)
   * [Adicionar pipelines de não produção](/help/using/non-production-pipelines.md)
   * [Editar um pipeline](/help/using/managing-pipelines.md#editing-pipelines)

   ![Repositório de código-fonte do pipeline e ramificação Git](/help/managing-code/assets/pipeline-repo-gitbranch.png)
   *Caixa de diálogo Adicionar pipeline de não produção com o repositório selecionado e a ramificação Git,*

1. Ao adicionar ou editar um pipeline, para especificar o local do **Código-fonte** para seu pipeline novo ou já existente, escolha o repositório externo que deseja usar na lista suspensa **Repositório**.

1. Na lista suspensa **Ramificação Git**, selecione a ramificação como a origem do pipeline.

1. Clique em **Salvar**.


>[!TIP]
>
>Para obter detalhes sobre como gerenciar repositórios no Cloud Manager, consulte [Repositórios do Cloud Manager](/help/managing-code/managing-repositories.md).


## Limitações

Repositórios externos não podem ser vinculados aos Pipelines de configuração.

<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY

* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->

