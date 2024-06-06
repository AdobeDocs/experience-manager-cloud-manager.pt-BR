---
title: Gerenciamento de repositórios no Cloud Manager
description: Saiba como criar, exibir e editar repositórios Git no Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: b15ef71ae24f51811798d2d25c8f75320e21c01f
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 27%

---


# Repositórios do Cloud Manager {#cloud-manager-repos}

Saiba como criar, exibir e editar repositórios Git no Cloud Manager.

## Visão geral {#overview}

Repositórios são usados para armazenar e gerenciar o código do seu projeto usando o Git. Todos os programas criados no Cloud Manager têm um repositório gerenciado por Adobe criado para eles.

Você pode optar por criar repositórios adicionais de gerenciamento de Adobe e também adicionar seus próprios repositórios privados. Todos os repositórios associados ao seu programa podem ser exibidos no **Repositórios** janela.

Os repositórios criados no Cloud Manager também estarão disponíveis para seleção ao adicionar ou editar pipelines. Consulte [Pipelines de CI-CD](/help/overview/ci-cd-pipelines.md) para saber mais.

Há um único repositório principal ou uma ramificação para um determinado pipeline. Com [suporte a submódulos Git,](git-submodules.md) muitas ramificações secundárias podem ser incluídas no momento da criação.

## Janela Repositórios {#repositories-window}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. No **Visão geral do programa** selecione a **Repositórios** para alternar para a guia **Repositórios** página.

1. A variável **Repositórios** exibe todos os repositórios associados ao seu programa.

   ![Janela Repositórios](assets/repositories.png)

A variável **Repositórios** fornece detalhes sobre os repositórios:

* O tipo de repositório
   * **Adobe** indica repositórios gerenciados por Adobe
   * **Privado** indica repositórios GitHub que você gerencia
* Quando foi criado
* Pipelines associados ao repositório

Você pode selecionar o repositório na janela e clicar no botão de reticências para realizar uma ação no repositório selecionado.

* **[Verificar ramificações/Criar projeto](#check-branches)** (disponível somente para repositórios Adobe)
* **[Copiar URL de repositório](#copy-url)**
* **[Exibir e atualizar](#view-update)**
* **[Excluir](#delete)**

![Ações do repositório](assets/repository-actions.png)

## Adicionar repositórios {#adding-repositories}

Toque ou clique no **Adicionar repositório** botão na caixa **Repositórios** janela para iniciar o **Adicionar repositório** assistente.

![Assistente para adicionar repositório](assets/add-repository-wizard.png)

O Cloud Manager oferece suporte a repositórios gerenciados pelo Adobe (**Repositório Adobe**), bem como seus próprios repositórios autogerenciados (**Repositório privado**). Os campos obrigatórios diferem dependendo do tipo de repositório que você escolher adicionar. Consulte os documentos a seguir para obter mais detalhes.

* [Adição de repositórios de Adobe no Cloud Manager](adobe-repositories.md)
* [Adição de repositórios privados no Cloud Manager](private-repositories.md)

>[!NOTE]
>
>* Um usuário deve ter a função **Gerente de implantação** ou **Proprietário da empresa** para poder adicionar um repositório.
>* Há um limite de 300 repositórios em todos os programas em uma determinada empresa ou organização IMS.

## Acessar informações do repositório {#repo-info}

Ao visualizar os repositórios no **Repositórios** você pode visualizar os detalhes sobre como acessar os repositórios gerenciados pelo Adobe de forma programática tocando ou clicando no link **Acessar informações do repositório** na barra de ferramentas.

![Informações do repositório](assets/access-repo-info.png)

A variável **Informações do repositório** é aberta com os detalhes. Para obter mais informações sobre o acesso às informações do repositório, consulte o documento [Acessando informações do repositório.](accessing-repositories.md)

## Verificar ramificações {#check-branches}

## Copiar URL de repositório {#copy-url}

A variável **Copiar URL de repositório** ação copia o URL do repositório selecionado na variável **Repositórios** para a área de transferência a ser usada em outro lugar.

## Visualizar e atualizar {#view-update}

A variável **Exibir e atualizar** ação abre a variável **Atualizar repositório** diálogo. Ao usá-lo, você pode visualizar as **Nome** e **Visualização do URL de repositório** e atualizar o **Descrição** do repositório.

![Exibir e atualizar informações do repositório](assets/update-repository.png)

## Excluir {#delete}

A variável **Excluir** A ação remove o repositório do projeto. Um repositório não pode ser excluído se estiver associado a um pipeline.

![Excluir](assets/delete.png)

Observe que, quando um repositório é excluído no Cloud Manager, ele é marcado como excluído e não é mais acessível ao usuário, mas é mantido no sistema para fins de recuperação.

Se você tentar criar um novo repositório depois de excluir um com o mesmo nome, receberá uma mensagem de erro `An error has occurred while trying to create repository. Please contact your CSE or Adobe Support.`

Se você receber esta mensagem de erro, entre em contato com o Suporte da Adobe para que o suporte possa ajudar a renomear o repositório excluído ou escolher um nome diferente para seu novo repositório.
