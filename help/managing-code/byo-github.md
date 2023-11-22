---
title: Trabalhar com seus próprios repositórios GitHub no Cloud Manager
description: Saiba como configurar o Cloud Manager para funcionar com seus próprios repositórios GitHub.
feature: Release Information
source-git-commit: 76a3dc6df41032488a3cfe11d0c72769562b96df
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 1%

---


# Trabalhar com seus próprios repositórios GitHub no Cloud Manager {#byo-github}

Ao configurar o Cloud Manager para funcionar com seus próprios repositórios GitHub, você pode validar seu código diretamente no repositório GitHub por meio do Cloud Manager, eliminando a necessidade de sincronizar consistentemente seu código com o repositório Adobe.

>[!NOTE]
>
>Este recurso só está disponível para [programa de adoção antecipada.](/help/release-notes/current.md#early-adoption)

## Configuração {#configuration}

A configuração consiste em duas etapas principais:

1. [Adicionar repositório](#add-repo)
1. [Validação de propriedade de repositório privado](#validate-ownership)

### Adicionar repositório {#add-repo}

1. No Cloud Manager, no **Visão geral do programa** toque ou clique em **Repositórios** para alternar para a guia **Repositórios** e clique em **Adicionar repositório**.

1. No **Adicionar repositório** , selecione **Repositório privado** como o tipo de repositório.

1. Forneça os detalhes do seu repositório

   * **Nome do repositório** - Um nome expressivo
   * **URL de repositório** - O URL do repositório, que deve terminar em `.git`
   * **Descrição** (opcional) - Uma descrição mais longa do repositório, conforme necessário

   ![Adicionar repositório próprio](/help/assets/repositories/add-own-github.png)

1. Toque ou clique em **Salvar**.

>[!TIP]
>
>Para obter detalhes sobre como gerenciar repositórios no Cloud Manager, consulte o documento [Repositórios do Cloud Manager.](/help/managing-code/repositories.md)

### Validação de propriedade de repositório privado {#validate-ownership}

O Cloud Manager agora sabe sobre o repositório GitHub, mas ainda precisa acessá-lo. Para conceder acesso, é necessário instalar o aplicativo GitHub do Adobe e verificar se você é o proprietário do repositório especificado.

1. Depois de adicionar seu próprio repositório, a variável **Validação de propriedade de repositório privado** será aberta.

   ![Validação de propriedade de repositório privado](/help/assets/repositories/private-repo-validate.png)

1. O Cloud Manager usa um aplicativo GitHub para interagir com segurança com seu repositório.
   * Um proprietário de sua organização GitHub deve instalar o aplicativo localizado em `https://github.com/apps/cloud-manager-for-aem-stage` e conceder acesso ao repositório.
   * Consulte a documentação do GitHub para obter detalhes sobre como isso é feito.

1. Para melhorar a segurança, você deve criar um arquivo secreto na ramificação padrão do seu repositório. Toque ou clique **Gerar**.

1. Confirme a geração do arquivo secreto tocando ou clicando em **Confirmar o**.

   ![Confirmar geração de segredo](/help/assets/repositories/confirm-generation.png)

1. De volta ao **Validação de propriedade de repositório privado** Cloud Manager gerou o conteúdo do arquivo privado na janela **Conteúdo do arquivo secreto** campo. Copie o conteúdo desse campo.

   * O conteúdo do arquivo secreto será mostrado apenas uma vez. Se você não copiar o conteúdo antes de fechar esta janela, precisará gerar o segredo novamente.

   ![Copiar conteúdo do arquivo secreto](/help/assets/repositories/new-secret.png)

1. Crie um novo arquivo na ramificação padrão do seu repositório GitHub chamada `.well-known/adobe/cloud-manager-challenge` e cole o conteúdo do arquivo secreto nesse arquivo e salve.

1. Depois que o aplicativo estiver instalado e o arquivo secreto existir no repositório, toque ou clique **Validar** no **Validação de propriedade de repositório privado** diálogo.

O aplicativo pode ser instalado e um arquivo secreto pode ser criado em qualquer ordem. No entanto, ambas as etapas devem ser concluídas para que você possa validar o.

Até a validação, o repositório será listado com um ícone vermelho, indicando que ainda não foi validado e não pode ser usado.

![Acordo de recompra não validado](/help/assets/repositories/unvalidated-repo.png)

Observe que **Tipo** A coluna identifica facilmente repositórios fornecidos por Adobe (**Adobe**) e seus próprios repositórios GitHub (**GitHub**).

Se precisar retornar ao repositório em uma data posterior para concluir a validação, no **Repositórios** toque ou clique no botão de reticências na linha que representa o repositório GitHub recém-adicionado e selecione **Validação de propriedade** no menu suspenso.

## Usar seus próprios repositórios GitHub com o Cloud Manager {#using}

Depois que o repositório GitHub é validado no Cloud Manager, a integração é concluída e você pode usar o repositório com o Cloud Manager.

1. Ao criar uma solicitação de pull, uma verificação do GitHub será iniciada automaticamente.

   ![Verificações do GitHub](/help/assets/repositories/github-checks.png)

1. Para cada pull request, um [pipeline de qualidade do código de pilha completa](/help/using/managing-pipelines.md) será criado automaticamente. Esse pipeline é iniciado a cada atualização de solicitação de pull.

1. A verificação do GitHub permanece em estado de execução até que as verificações de qualidade do código sejam concluídas. Os resultados de qualidade do código serão propagados para a verificação do GitHub.

   ![Verificações de qualidade do código do GitHub](/help/assets/repositories/github-code-quality.png)

Quando a solicitação de pull é fechada ou mesclada, o pipeline de qualidade do código de pilha completa criado é excluído automaticamente.

## Limitações {#limitations}

Lembre-se das seguintes limitações ao usar seus próprios repositórios GitHub com o Cloud Manager.

* Não é possível usar os repositórios GitHub como a fonte direta do repositório para os pipelines que você gerencia.
   * Essa funcionalidade está planejada.
* Não é possível pausar a validação da solicitação de pull usando a verificação do GitHub no Cloud Manager.
   * Se o repositório GitHub for validado no Cloud Manager, o Cloud Manager sempre tentará validar as solicitações de pull criadas para esse repositório.
Se o aplicativo GitHub Adobe for removido da organização GitHub, o recurso de validação de solicitações de pull será removido para todos os repositórios.