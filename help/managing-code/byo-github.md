---
title: Trabalhe com os seus repositórios do GitHub no Cloud Manager
description: Saiba como configurar o Cloud Manager para trabalhar com os seus repositórios do GitHub.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: 3bb59686a3c25e47e5c747bb8d5f626055e54a06
workflow-type: ht
source-wordcount: '753'
ht-degree: 100%

---


# Trabalhe com os seus repositórios do GitHub no Cloud Manager {#byo-github}

Ao configurar o Cloud Manager para trabalhar com os seus repositórios do GitHub, você pode validar o código diretamente no repositório do GitHub por meio do Cloud Manager, eliminando a necessidade de sincronizar consistentemente o código com o repositório da Adobe.

>[!NOTE]
>
>Este recurso só está disponível por meio do [programa de adoção antecipada.](/help/release-notes/current.md#early-adoption)

## Configuração {#configuration}

A configuração consiste em duas etapas principais:

1. [Adicionar repositório](#add-repo)
1. [Validação de propriedade de repositório privado](#validate-ownership)

### Adicionar repositório {#add-repo}

1. Na página **Visão geral do programa** do Cloud Manager, toque ou clique na guia **Repositórios** para alternar para a página **Repositórios** e clique em **Adicionar repositório**.

1. Na caixa de diálogo **Adicionar repositório**, selecione **Repositório privado** como o tipo de repositório.

1. Forneça os detalhes do repositório

   * **Nome do repositório**: um nome intuitivo
   * **URL do repositório**: o URL do repositório, que deve terminar em `.git`
   * **Descrição** (opcional): uma descrição mais longa do repositório, conforme necessário

   ![Adicionar repositório próprio](/help/assets/repositories/add-own-github.png)

1. Toque ou clique em **Salvar**.

>[!TIP]
>
>Para obter detalhes sobre como gerenciar repositórios no Cloud Manager, consulte o documento [Repositórios do Cloud Manager.](/help/managing-code/repositories.md)

### Validação de propriedade de repositório privado {#validate-ownership}

O Cloud Manager agora reconhece seu repositório GitHub, mas ainda precisa de acesso. Para conceder acesso, é necessário instalar o aplicativo GitHub da Adobe e confirmar que você é proprietário(a) do repositório especificado.

1. Após adicionar seu próprio repositório, a caixa de diálogo **Validação de propriedade de repositório privado** será aberta.

   ![Validação de propriedade de repositório privado](/help/assets/repositories/private-repo-validate.png)

1. O Cloud Manager usa um aplicativo GitHub para interagir de maneira segura com o repositório.
   * Um(a) proprietário(a) de sua organização do GitHub deve instalar o aplicativo localizado em `https://github.com/apps/cloud-manager-for-aem` e conceder acesso ao repositório.
   * Consulte a documentação do GitHub para obter detalhes sobre como fazer isso.

1. Para melhorar a segurança, você deve criar um arquivo secreto na ramificação padrão do repositório. Toque ou clique em **Gerar**.

1. Confirme a geração do arquivo secreto tocando ou clicando em **Confirmar**.

   ![Confirmar geração de segredo](/help/assets/repositories/confirm-generation.png)

1. De volta à janela **Validação de propriedade de repositório privado**, o Cloud Manager terá gerado o conteúdo do arquivo privado no campo **Conteúdo do arquivo secreto**. Copie o conteúdo desse campo.

   * O conteúdo do arquivo secreto será mostrado apenas uma vez. Se você não copiar o conteúdo antes de fechar esta janela, precisará gerar o segredo novamente.

   ![Copiar conteúdo do arquivo secreto](/help/assets/repositories/new-secret.png)

1. Crie um novo arquivo na ramificação padrão do repositório GitHub chamado `.well-known/adobe/cloud-manager-challenge`, cole o conteúdo do arquivo secreto nesse arquivo e salve.

1. Após a instalação do aplicativo e a adição do arquivo secreto no repositório, toque ou clique em **Validar** na caixa de diálogo **Validação de propriedade de repositório privado**.

A instalação do aplicativo e criação do arquivo secreto podem ser realizadas em qualquer ordem. No entanto, ambas as etapas devem ser concluídas para que você possa validar.

Até a validação, o repositório será listado com um ícone vermelho, indicando que ainda não foi validado e não pode ser usado.

![Repositório não validado](/help/assets/repositories/unvalidated-repo.png)

Observe que a coluna **Tipo** identifica facilmente os repositórios fornecidos pela Adobe (**Adobe**) e os seus repositórios do GitHub (**GitHub**).

Se precisar retornar ao repositório em uma data posterior para concluir a validação, na página **Repositórios**, toque ou clique no botão de reticências na linha que representa o repositório GitHub recém-adicionado e selecione **Validação de propriedade** no menu suspenso.

## Use seus repositórios do GitHub com o Cloud Manager {#using}

Após a validação do repositório do GitHub no Cloud Manager, a integração é concluída e é possível usar o repositório com o Cloud Manager.

1. Ao criar uma solicitação de “pull”, uma verificação do GitHub será iniciada automaticamente.

   ![Verificações do GitHub](/help/assets/repositories/github-checks.png)

1. Para cada solicitação de “pull”, um [pipeline de qualidade de código de pilha completa](/help/using/managing-pipelines.md) será criado automaticamente. Esse pipeline é iniciado a cada atualização de solicitação de “pull”.

1. A verificação do GitHub permanece em estado de execução até que as verificações de qualidade do código sejam concluídas. Os resultados de qualidade do código serão propagados para a verificação do GitHub.

   ![Verificações de qualidade do código do GitHub](/help/assets/repositories/github-code-quality.png)

Quando a solicitação de “pull” é fechada ou mesclada, o pipeline de qualidade de código de pilha completa criado é excluído automaticamente.

## Limitações {#limitations}

Lembre-se das seguintes limitações ao usar os seus repositórios do GitHub com o Cloud Manager.

* Não é possível usar os repositórios do GitHub como a fonte de repositório direta dos pipelines que você gerencia.
   * Essa funcionalidade está planejada.
* Não é possível pausar a validação da solicitação de “pull” usando a verificação do GitHub no Cloud Manager.
   * Se o repositório do GitHub for validado no Cloud Manager, o Cloud Manager sempre tentará validar as solicitações de “pull” criadas para esse repositório.
Se o aplicativo GitHub da Adobe for removido de sua organização do GitHub, o recurso de validação de solicitações de “pull” será removido de todos os repositórios.
