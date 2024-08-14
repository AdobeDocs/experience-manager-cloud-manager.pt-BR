---
title: Adicionar repositórios privados no Cloud Manager
description: Saiba como configurar o Cloud Manager para trabalhar com os seus repositórios do GitHub.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 38%

---


# Adicionar repositórios privados no Cloud Manager {#private-repositories}

Saiba como configurar o Cloud Manager para trabalhar com os seus repositórios do GitHub.

## Visão geral {#overview}

Configurar o Cloud Manager com seus repositórios GitHub privados permite validar o código diretamente no GitHub, eliminando a necessidade de sincronização com o repositório Adobe com frequência.

>[!NOTE]
>
>Esse recurso é exclusivo do GitHub público. A compatibilidade com o GitHub auto-hospedado não está disponível.

## Configuração {#configuration}

A configuração consiste em duas etapas principais:

1. [Adicionar repositório](#add-repo)
1. [Validação de propriedade de repositório privado](#validate-ownership)

### Adicionar repositório {#add-repo}

1. Na Cloud Manager, na página **Visão geral do programa**, clique na guia **Repositórios** para alternar para a página **Repositórios** e clique em **Adicionar repositório**.

1. Na caixa de diálogo **Adicionar repositório**, selecione **Repositório privado** como o tipo de repositório.

1. Forneça os detalhes do repositório

   * **Nome do repositório**: um nome intuitivo
   * **URL do repositório**: o URL do repositório, que deve terminar em `.git`
   * **Descrição** (opcional): uma descrição mais longa do repositório, conforme necessário

   ![Adicionar repositório próprio](/help/assets/repositories/add-own-github.png)

1. Clique em **Salvar**.

>[!TIP]
>
>Para obter detalhes sobre como gerenciar repositórios no Cloud Manager, consulte [Repositórios Cloud Manager](/help/managing-code/managing-repositories.md).

### Validação de propriedade de repositório privado {#validate-ownership}

O Cloud Manager agora reconhece seu repositório GitHub, mas ainda precisa de acesso. Para conceder acesso, é necessário instalar o aplicativo GitHub da Adobe e confirmar que você é proprietário(a) do repositório especificado.

1. Depois de adicionar seu próprio repositório, a caixa de diálogo **Validação da Propriedade do Repositório Privado** é exibida.

   ![Validação de propriedade de repositório privado](/help/assets/repositories/private-repo-validate.png)

1. O Cloud Manager usa um aplicativo GitHub para interagir com seu repositório de forma segura.

   Um proprietário de sua organização do GitHub deve instalar o aplicativo localizado em `https://github.com/apps/cloud-manager-for-aem` e conceder acesso ao repositório. Consulte a documentação do GitHub para obter mais detalhes.

1. Para melhorar a segurança, crie um arquivo secreto na ramificação padrão do seu repositório. Clique em **Gerar**.

1. Confirme a geração do arquivo secreto clicando em **Confirmar**.

   ![Confirmar geração de segredo](/help/assets/repositories/confirm-generation.png)

1. De volta à caixa de diálogo **Validação de Propriedade de Repositório Privado**, o Cloud Manager gerou o conteúdo no campo **Conteúdo do arquivo secreto**. Copie o conteúdo desse campo.

   O conteúdo do arquivo secreto é mostrado apenas uma vez. Se você não copiar o conteúdo antes de fechar esta janela, deverá gerar o segredo novamente.

   ![Copiar conteúdo do arquivo secreto](/help/assets/repositories/new-secret.png)

1. Crie um novo arquivo na ramificação padrão do repositório GitHub chamado `.well-known/adobe/cloud-manager-challenge`, cole o conteúdo do arquivo secreto nesse arquivo e salve.

1. Depois que o aplicativo for instalado e o arquivo secreto existir no repositório, você poderá clicar em **Validar** na caixa de diálogo **Validação de Propriedade de Repositório Privado**.

O aplicativo pode ser instalado e você pode gerar um arquivo secreto em qualquer ordem. No entanto, ambas as etapas devem ser concluídas para que você possa validar o.

Até a validação, o repositório é listado com um ícone vermelho, indicando que ainda não foi validado e não pode ser usado.

![Repositório não validado](/help/assets/repositories/unvalidated-repo.png)

Observe que a coluna **Tipo** identifica facilmente os repositórios fornecidos pela Adobe (**Adobe**) e os seus repositórios do GitHub (**GitHub**).

Para retornar ao repositório mais tarde e concluir a validação, vá para a página **Repositórios**. Clique no botão de reticências ao lado do repositório GitHub adicionado e selecione **Validação de propriedade** no menu suspenso.

## Usar repositórios privados com o Cloud Manager {#using}

Depois que o repositório GitHub for validado no Cloud Manager, a integração será concluída e você poderá usar o repositório com o Cloud Manager.

1. Ao criar uma solicitação de pull, uma verificação do GitHub é iniciada automaticamente.

   ![Verificações do GitHub](/help/assets/repositories/github-checks.png)

1. Para cada solicitação de pull, um [pipeline de qualidade de código de pilha completa](/help/using/managing-pipelines.md) é criado automaticamente. Esse pipeline é iniciado a cada atualização de solicitação de pull.

1. A verificação do GitHub permanece em estado de execução até que as verificações de qualidade do código sejam concluídas. Os resultados de qualidade do código são propagados para a verificação do GitHub.

   ![Verificações de qualidade do código do GitHub](/help/assets/repositories/github-code-quality.png)

Quando a solicitação de “pull” é fechada ou mesclada, o pipeline de qualidade de código de pilha completa criado é excluído automaticamente.

>[!TIP]
>
>Consulte o documento [Anotações de verificação do GitHub](github-annotations.md) para obter detalhes sobre as informações fornecidas pelo GitHub quando as verificações de solicitação de pull são executadas.

>[!TIP]
>
>Você pode controlar os pipelines criados automaticamente para validar cada solicitação de pull para um repositório privado. Consulte [Configuração de verificação do GitHub para repositórios privados](github-check-config.md) para obter mais informações.

## Associar repositórios privados a pipelines {#pipelines}

Repositórios privados validados podem ser associados a [pipelines de pilha completa](/help/overview/ci-cd-pipelines.md).

## Limitações {#limitations}

Certas limitações se aplicam ao uso de repositórios privados com o Cloud Manager.

* Não é possível pausar a validação da solicitação de pull usando a verificação do GitHub da Cloud Manager. Se o repositório GitHub for validado no Cloud Manager, o Cloud Manager tentará validar as solicitações de pull criadas para esse repositório.
* Se o aplicativo GitHub Adobe for removido da organização GitHub, essa ação removerá o recurso de validação de solicitações de pull para todos os repositórios.
* Nenhuma tag do Git é criada e enviada ao usar repositórios privados em pipelines de pilha completa de produção.
* Os pipelines que usam repositórios privados e o acionador de build ao confirmar não são iniciados automaticamente quando uma nova confirmação é enviada para a ramificação selecionada.
* A [Funcionalidade de reutilização de artefato](/help/getting-started/project-setup.md#build-artifact-reuse) não se aplica a repositórios privados.
