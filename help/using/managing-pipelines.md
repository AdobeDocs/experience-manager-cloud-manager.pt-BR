---
title: Gerenciar pipelines
description: Saiba como gerenciar os pipelines existentes, incluindo edição, execução e exclusão.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 28ab641ec85335d8330aeb465c07bf0264218fe4
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 67%

---


# Gerenciar pipelines {#managing-pipelines}

Saiba como gerenciar os pipelines existentes, incluindo edição, execução e exclusão.

## Cartão Pipelines {#pipeline-card}

O cartão **Pipelines** na página **Visão geral do programa** no Cloud Manager fornece uma visão geral de todos os seus pipelines e seu status atual.

![Cartão Pipelines no Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Ao clicar no botão de reticências ao lado de cada pipeline, você pode realizar as ações a seguir.

* [Executar o pipeline](#running-pipelines)
* [Editar o pipeline](#editing-pipelines)
* [Excluir o pipeline](#deleting-pipelines)
* [Exibir detalhes](#view-details)

Na parte inferior da lista de pipelines, você tem opções gerais.

* **Adicionar** - Para [adicionar um novo pipeline de produção](/help/using/production-pipelines.md) ou [adicionar novo pipeline de não produção](/help/using/non-production-pipelines.md)
* **Exibir todos** - Leva o usuário para os **Pipelines** para exibir todos os pipelines em uma tabela mais detalhada
* **Acessar informações do repositório** - Exibe as informações necessárias para acessar o repositório Git do Cloud Manager
* **Saiba mais** - Navega até os recursos de documentação do pipeline de CI/CD.

## Janela Pipelines {#pipelines}

A variável **Pipelines** A janela mostra uma lista completa de todos os pipelines para o programa selecionado. Isso é útil, pois apresenta informações mais abrangentes do que as disponíveis no [Cartão Pipeline.](#pipeline-card)

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. No **Visão geral do programa** toque ou clique em **Pipelines** para alternar para a guia **Pipelines** janela.

1. Aqui você pode ver uma lista de todos os pipelines para o programa, bem como iniciar e parar a execução do pipeline, como faria na variável **Cartão Pipelines**.

Se um pipeline estiver em execução, passar o mouse sobre ele **Status** revelará detalhes sobre a execução.

![Detalhes de execução do pipeline](/help/assets/configure-pipelines/pipeline-status.png)

Tocar ou clicar **Exibir detalhes** levará você ao [detalhes da execução do pipeline.](#view-details)

## Janela de atividade {#activity}

A variável **Atividades** A janela mostra uma lista completa de todas as execuções de pipelines para o programa selecionado.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. No **Visão geral do programa** toque ou clique em **Atividade** para alternar para a guia **Atividade** janela.

1. Aqui você pode ver uma lista de todas as execuções de pipeline do programa, incluindo as execuções atuais e históricas.

Se um pipeline estiver em execução, passar o mouse sobre ele **Status** revelará detalhes sobre a execução.

![Detalhes de execução do pipeline](/help/assets/configure-pipelines/pipeline-activity.png)

Tocar ou clicar **Exibir detalhes** levará você ao [detalhes da execução do pipeline.](#view-details)

## Execução de pipelines {#running-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. Navegue até o cartão **Pipelines** na página **Visão geral do programa** e clique no botão de reticências ao lado do pipeline que deseja executar e selecione **Executar** no menu.

1. A execução do pipeline começa e é indicada pela coluna **Status**.

Você pode ver os detalhes da execução clicando no botão de reticências novamente e selecionando **[Exibir detalhes](#view-details)**.

Dependendo do tipo de pipeline, talvez seja possível cancelar a execução clicando no botão de reticências novamente e selecionando **Cancelar**.

## Edição de pipelines {#editing-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. Navegue até o cartão **Pipelines** na página **Visão geral do programa** e clique no botão de reticências ao lado do pipeline que deseja editar e selecione **Editar** no menu.

1. A caixa de diálogo **Editar pipeline de produção** ou **Editar pipeline de não produção** é exibida, permitindo editar os mesmos detalhes inseridos ao criar o pipeline.

   * Consulte as páginas a seguir para obter detalhes sobre todos os campos e opções de configuração disponíveis para pipelines.
      * [Configuração de pipelines de produção](/help/using/production-pipelines.md)
      * [Configurar pipelines de não produção](/help/using/non-production-pipelines.md)

1. Clique em **Atualizar** depois de concluir a edição do pipeline.

>[!NOTE]
>
>Não é possível editar um pipeline em execução.

## Exclusão de pipelines {#deleting-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. Navegue até o cartão **Pipelines** na página **Visão geral do programa** e clique no botão de reticências ao lado do pipeline executado e selecione **Excluir** no menu.

>[!NOTE]
>
>Não é possível excluir um pipeline em execução.

## Exibir Detalhes {#view-details}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. Navegue até o cartão **Pipelines** na página **Visão geral do programa** e clique no botão de reticências ao lado do pipeline executado e selecione **Exibir detalhes** no menu.

1. Você será levado à página de detalhes do pipeline em execução.

![Detalhes do pipeline](/help/assets/configure-pipelines/pipeline-running-details.png)

Desse ponto, você poderá ver o status das várias etapas do pipeline e recuperar registros de criação para fins de diagnóstico. Consulte o documento [Implantação do código](/help/using/code-deployment.md) para obter mais informações.

Todas as etapas em uma execução de pipeline são exibidas com aquelas que ainda não foram iniciadas esmaecidas. As etapas concluídas exibem sua duração.

Quando uma etapa do pipeline é concluída, um resumo é apresentado.

![Resumo da etapa](/help/assets/configure-pipelines/pipeline-step.png)

Toque ou clique no **Exibir detalhes** link para revelar a **Duração** seção. Isso inclui a duração média do pipeline com base na tendência histórica para esse programa.

![Duração](/help/assets/configure-pipelines/duration.png)

>[!NOTE]
>
>Você somente pode exibir detalhes de um pipeline que está em execução ou que foi executado pelo menos uma vez.
