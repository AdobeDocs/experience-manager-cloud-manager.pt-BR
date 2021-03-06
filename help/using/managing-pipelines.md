---
title: Gerenciar pipelines
description: Saiba como gerenciar seus pipelines existentes, incluindo edição, execução e exclusão.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 99325c28c379103db2ba4c19bb6d206849c6e126
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 3%

---


# Gerenciar pipelines {#managing-pipelines}

Saiba como gerenciar seus pipelines existentes, incluindo edição, execução e exclusão.

## Placa pipeline {#pipeline-card}

O **Pipelines** no cartão **Visão geral do programa** no Cloud Manager fornece uma visão geral de todos os seus pipelines e seu status atual.

![Cartão de pipeline no Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Ao clicar no botão de reticências ao lado de cada pipeline, você pode realizar as seguintes ações.

* [Executar o pipeline](#running-pipelines)
* [Editar o pipeline](#editing-pipelines)
* [Excluir o pipeline](#deleting-pipelines)
* [Exibir detalhes](#view-details)

Na parte inferior da lista de pipelines, você tem opções gerais.

* **Adicionar** - Para [adicionar um novo pipeline de produção](/help/using/production-pipelines.md) ou [adicionar novo pipeline de não produção](/help/using/non-production-pipelines.md)
* **Mostrar tudo** - Leva o usuário para a **Pipelines** para exibir todos os pipelines em uma tabela mais detalhada
* **Acessar informações do repositório** - Exibe as informações necessárias para acessar o repositório Git do Cloud Manager
* **Saiba mais** - Navega até os recursos de documentação do pipeline de CI/CD.

## Executando Pipelines {#running-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o **Pipelines** do cartão **Visão geral do programa** e clique no botão de reticências ao lado do pipeline que você executa , selecione **Executar** no menu .

1. A execução do pipeline começa e é indicada pela variável **Status** coluna.

Você pode ver os detalhes da execução clicando no botão de reticências novamente e selecionando **[Exibir detalhes.](#view-details)**

Dependendo do tipo de pipeline, talvez seja possível cancelar a execução clicando no botão de reticências novamente e selecionando **Cancelar**.

## Edição de pipeline {#editing-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o **Pipelines** do cartão **Visão geral do programa** clique no botão de reticências ao lado do pipeline que deseja editar e selecione **Editar** no menu .

1. O **Editar pipeline de produção** ou **Editar pipeline de não produção** é exibida, permitindo editar os mesmos detalhes inseridos ao criar o pipeline.

   * Consulte as páginas a seguir para obter detalhes sobre todos os campos e opções de configuração disponíveis para pipelines.
      * [Configuração de pipeline de produção](/help/using/production-pipelines.md)
      * [Configuração de pipeline de não produção](/help/using/non-production-pipelines.md)

1. Clique em **Atualizar** depois de concluir a edição do pipeline.

>[!NOTE]
>
>Não é possível editar um pipeline em execução.

## Exclusão de pipeline {#deleting-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o **Pipelines** do cartão **Visão geral do programa** e clique no botão de reticências ao lado do pipeline que você executa , selecione **Excluir** no menu .

>[!NOTE]
>
>Não é possível excluir um pipeline em execução.

## Visualizar Detalhes {#view-details}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o **Pipelines** do cartão **Visão geral do programa** e clique no botão de reticências ao lado do pipeline que você executa , selecione **Exibir detalhes** no menu .

1. Você é levado à página de detalhes do pipeline em execução.

![Detalhes do pipeline](/help/assets/configure-pipelines/pipeline-running-details.png)

Desse ponto, você pode ver o status das várias etapas do pipeline e recuperar registros de criação para fins de diagnóstico. Consulte o documento [Implantação do código](/help/using/code-deployment.md) para obter mais informações.

>[!NOTE]
>
>Você só pode exibir detalhes de um pipeline que está em execução ou foi executado pelo menos uma vez.
