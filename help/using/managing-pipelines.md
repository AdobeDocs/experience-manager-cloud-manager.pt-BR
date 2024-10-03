---
title: Gerenciar pipelines
description: Saiba como gerenciar seus pipelines existentes, incluindo execução, edição e exclusão.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 9d910e1b1a4aad000a8389ddc22ce380bbccd4ef
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 89%

---


# Gerenciar pipelines {#managing-pipelines}

Saiba como gerenciar seus pipelines existentes, incluindo execução, edição e exclusão.

## Cartão do pipeline {#pipeline-card}

O cartão **Pipelines** na página **Visão geral do programa** no Cloud Manager fornece uma visão geral de todos os seus pipelines e seu status atual.

![Cartão Pipelines no Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Ao clicar no botão de reticências ao lado de cada pipeline, você pode realizar as seguintes ações:

* [Executar o pipeline](#running-pipelines).
* [Editar o pipeline](#editing-pipelines).
* [Excluir o pipeline](#deleting-pipelines).
* [Exibir detalhes](#view-details).

Na parte inferior da lista de pipelines, você tem as seguintes opções gerais.

* **Adicionar**: para [adicionar um novo pipeline de produção](/help/using/production-pipelines.md) ou [adicionar novo pipeline de não produção](/help/using/non-production-pipelines.md).
* **Exibir todos**: leva o usuário para a tela **Pipelines** para exibir todos os pipelines em uma tabela mais detalhada
* **Acessar informações do repositório**: Exibe as informações necessárias para acessar o repositório Git do Cloud Manager.
* **Saiba mais**: Navega até os recursos de documentação do pipeline de CI/CD.

## Página Pipelines {#pipelines}

A página **Pipelines** mostra uma lista completa de todos os pipelines do programa selecionado. Esta lista é útil porque apresenta informações mais abrangentes que as disponíveis no [cartão do pipeline](#pipeline-card).

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Na página **Visão geral do programa**, clique na guia **Pipelines** para alternar para a página **Pipelines**.

1. Nessa janela você pode ver uma lista de todos os pipelines do programa, bem como iniciar e parar a execução do pipeline, assim como no **cartão do pipeline**.

Clicar no ícone `i` revela detalhes sobre a última execução ou a execução atual do pipeline.

![Detalhes da execução do pipeline](/help/assets/configure-pipelines/pipeline-status.png)

Clicar em **Exibir detalhes** mostrará os [detalhes da execução do pipeline](#view-details).

## Página Atividade {#activity}

A página **Atividades** mostra uma lista completa de todas as execuções de pipelines para o programa selecionado.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Na página **Visão geral do programa**, clique na guia **Atividade** para alternar para a página **Atividade**.

1. Aqui você pode ver uma lista de todas as execuções de pipeline do programa, incluindo as execuções atuais e históricas.

Clicar no ícone `i` revela detalhes sobre a execução do pipeline selecionado.

![Detalhes da execução do pipeline](/help/assets/configure-pipelines/pipeline-activity.png)

Clique em **Exibir detalhes** para revisar os [detalhes da execução do pipeline](#view-details).

## Executar pipelines {#running-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.
1. Navegue até o cartão **Pipelines** na página **Visão geral do programa**.
1. Clique no botão de reticências ao lado do pipeline que você está executando e, no menu, selecione **Executar**.

   A coluna Status indica quando a execução do pipeline começa.

   Você pode ver os detalhes da execução clicando no botão de reticências novamente e selecionando **[Exibir detalhes](#view-details)**.

   Dependendo do tipo de pipeline, talvez seja possível cancelar a execução clicando no botão de reticências novamente e selecionando **Cancelar**.

## Editar pipelines {#editing-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o cartão **Pipelines** da página **Visão geral do programa**, clique no botão de reticências ao lado do pipeline que deseja editar e selecione **Editar** no menu.

1. A caixa de diálogo **Editar pipeline de produção** ou **Editar pipeline de não produção** é exibida. Você pode editar os mesmos detalhes inseridos durante a criação do pipeline.

   Consulte [Configuração de pipelines de produção](/help/using/production-pipelines.md) e [Configuração de pipelines de não produção](/help/using/non-production-pipelines.md) para obter detalhes sobre os campos e as opções de configuração disponíveis para pipelines.

1. Clique em **Atualizar** quando terminar.

>[!NOTE]
>
>Não é possível editar um pipeline em execução.

## Excluir pipelines {#deleting-pipelines}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o cartão **Pipelines** da página **Visão geral do programa**, clique no botão de reticências ao lado do pipeline executado e selecione **Excluir** no menu.

>[!NOTE]
>
>Não é possível excluir um pipeline em execução.

## Exibir detalhes {#view-details}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o cartão **Pipelines** da página **Visão geral do programa**, clique no botão de reticências ao lado do pipeline executado e selecione **Exibir detalhes** no menu.

1. Você será levado à página de detalhes do pipeline em execução.

![Detalhes do pipeline](/help/assets/configure-pipelines/pipeline-running-details.png)

Aqui, você pode ver o status das várias etapas do pipeline e recuperar logs de build para fins de diagnóstico. Consulte o documento [Implantação do código](/help/using/code-deployment.md) para obter mais informações.

Ao exibir todas as etapas de uma execução de pipeline, as que ainda não foram iniciadas aparecem esmaecidas. As etapas concluídas exibem sua duração.

Quando uma etapa do pipeline é concluída, um resumo é apresentado.

![Resumo da etapa](/help/assets/configure-pipelines/pipeline-step.png)

Clique no link **Exibir detalhes** para revelar a seção **Duração**. Esta seção inclui a duração média do pipeline com base na tendência histórica para esse programa.

![Duração](/help/assets/configure-pipelines/duration.png)

Se o pipeline tiver uma etapa de **Varredura de código** que gerou problemas, clique no botão **Detalhes de download** para exibir uma lista de [testes de qualidade do código](/help/using/code-quality-testing.md) não aprovados.

![Problemas de qualidade do código](assets/managing-pipelines-code-quality-issues.png)

Uma coluna **Localização do arquivo do projeto** está disponível no arquivo CSV para indicar a localização do código incorreto. Essa coluna é o caminho relativo do projeto, enquanto a coluna **Localização do arquivo** é gerada pelo Maven.

![Detalhes do problema de verificação do código do projeto](assets/managing-pipelines-code-quality-details.png)


>[!NOTE]
>
>Só é possível exibir detalhes de um pipeline que está em execução ou que foi executado pelo menos uma vez.
