---
title: Gerenciar pipelines
description: Saiba como gerenciar os pipelines existentes, incluindo edição, execução e exclusão.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 8e2c57d2594691e7fb18d8a538caa9b54a26b6bb
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 41%

---


# Gerenciar pipelines {#managing-pipelines}

Saiba como gerenciar os pipelines existentes, incluindo edição, execução e exclusão.

## Cartão Pipeline {#pipeline-card}

O cartão **Pipelines** na página **Visão geral do programa** no Cloud Manager fornece uma visão geral de todos os seus pipelines e seu status atual.

![Cartão Pipelines no Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Ao clicar no botão de reticências ao lado de cada pipeline, você pode realizar as seguintes ações:

* [Executar o pipeline](#running-pipelines).
* [Editar o pipeline](#editing-pipelines).
* [Excluir o pipeline](#deleting-pipelines).
* [Exibir detalhes](#view-details).

Na parte inferior da lista de pipelines, você tem as seguintes opções gerais.

* **Adicionar** - A [adicionar um novo pipeline de produção](/help/using/production-pipelines.md) ou [adicionar um novo pipeline de não produção](/help/using/non-production-pipelines.md).
* **Mostrar tudo** - Leva o usuário para os **Pipelines** para exibir todos os pipelines em uma tabela mais detalhada.
* **Acessar informações do repositório** - Exibe as informações necessárias para acessar o repositório Git do Cloud Manager.
* **Saiba mais** - Navega até os recursos de documentação do pipeline de CI/CD.

## Janela Pipelines {#pipelines}

A janela **Pipelines** mostra uma lista completa de todos os pipelines do programa selecionado. Esta lista é útil porque apresenta informações mais abrangentes do que as disponíveis no [cartão Pipelines](#pipeline-card).

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Na página **Visão geral do programa**, clique na guia **Pipelines** para alternar para a janela **Pipelines**.

1. Aqui você pode ver uma lista de todos os pipelines para o programa e iniciar e parar a execução do pipeline como faria no **Cartão Pipelines**.

Clicar no ícone `i` revela detalhes sobre a última execução ou a execução atual do pipeline.

![Detalhes da execução do pipeline](/help/assets/configure-pipelines/pipeline-status.png)

Clicar em **Exibir detalhes** leva você aos [detalhes da execução do pipeline](#view-details).

## Janela Atividade {#activity}

A janela **Atividades** mostra uma lista completa de todas as execuções de pipeline do programa selecionado.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. Na página **Visão geral do programa**, clique na guia **Atividade** para alternar para a janela **Atividade**.

1. Aqui você pode ver uma lista de todas as execuções de pipeline do programa, incluindo as execuções atuais e históricas.

Clicar no ícone `i` revela detalhes sobre a execução do pipeline selecionado.

![Detalhes da execução do pipeline](/help/assets/configure-pipelines/pipeline-activity.png)

Clique em **Exibir detalhes** para revisar [detalhes da execução do pipeline](#view-details).

## Executar pipelines {#running-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.
1. Navegue até o cartão **Pipelines** na página **Visão geral do programa**.
1. Clique no botão de reticências ao lado do pipeline que você está executando e, no menu, selecione **Executar**.

   A coluna Status indica quando a execução do pipeline começa.

   Você pode ver os detalhes da execução clicando no botão de reticências novamente e selecionando **[Exibir detalhes](#view-details)**.

   Dependendo do tipo de pipeline, talvez seja possível cancelar a execução clicando no botão de reticências novamente e selecionando **Cancelar**.

## Editar pipelines {#editing-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o cartão **Pipelines** da página **Visão geral do programa** e clique no botão de reticências ao lado do pipeline que deseja editar e, no menu, selecione **Editar**.

1. A caixa de diálogo **Editar pipeline de produção** ou **Editar pipeline de não produção** é exibida. Você pode editar os mesmos detalhes inseridos durante a criação do pipeline.

   Consulte [Configurando Pipelines de Produção](/help/using/production-pipelines.md) e [Configurando Pipelines de Não Produção](/help/using/non-production-pipelines.md) para obter detalhes sobre os campos e as opções de configuração disponíveis para pipelines.

1. Clique em **Atualizar** quando terminar.

>[!NOTE]
>
>Não é possível editar um pipeline em execução.

## Excluir pipelines {#deleting-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o cartão **Pipelines** da página **Visão geral do programa** e clique no botão de reticências ao lado do pipeline executado e, no menu, selecione **Excluir**.

>[!NOTE]
>
>Não é possível excluir um pipeline em execução.

## Exibir detalhes {#view-details}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o cartão **Pipelines** da página **Visão geral do programa** e clique no botão de reticências ao lado do pipeline executado e, no menu, selecione **Exibir detalhes**.

1. Você será levado à página de detalhes do pipeline em execução.

![Detalhes do pipeline](/help/assets/configure-pipelines/pipeline-running-details.png)

Aqui, você pode ver o status das várias etapas do pipeline e recuperar registros de compilação para fins de diagnóstico. Consulte o documento [Implantação do código](/help/using/code-deployment.md) para obter mais informações.

Ao exibir todas as etapas de uma execução de pipeline, as que ainda não foram iniciadas aparecem esmaecidas. As etapas concluídas exibem sua duração.

Quando uma etapa do pipeline é concluída, um resumo é apresentado.

![Resumo da etapa](/help/assets/configure-pipelines/pipeline-step.png)

Clique no link **Exibir detalhes** para revelar a seção **Duração**. Esta seção inclui a duração média do pipeline com base na tendência histórica para esse programa.

![Duração](/help/assets/configure-pipelines/duration.png)

Se seu pipeline continha uma etapa de **Verificação de código**, o que gerou problemas, você pode clicar no botão **Detalhes do download** para exibir uma lista de [testes de qualidade do código](/help/using/code-quality-testing.md) que não foram aprovados.

![Problemas de qualidade do código](assets/managing-pipelines-code-quality-issues.png)

Uma coluna **Localização do arquivo do projeto** está disponível no arquivo CSV para indicar a localização do código incorreto. Essa coluna é o caminho relativo do projeto, enquanto a coluna **Localização do arquivo** é gerada pelo Maven.

![Detalhes do problema de verificação do código do projeto](assets/managing-pipelines-code-quality-details.png)


>[!NOTE]
>
>Só é possível exibir detalhes de um pipeline que está em execução ou que foi executado pelo menos uma vez.
