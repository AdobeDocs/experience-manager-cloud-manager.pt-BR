---
title: Cópia de conteúdo para consistência do ambiente
description: A ferramenta de cópia de conteúdo do Cloud Manager Adobe permite que os usuários copiem conteúdo mutável sob demanda de ambientes de produção Adobe Experience Manager 6.x hospedados na Managed Services para ambientes inferiores para testes.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 2c96feb62a4db2424430c9c410563a7f61320fd2
workflow-type: tm+mt
source-wordcount: '1364'
ht-degree: 41%

---


# Cópia de conteúdo para consistência do ambiente {#content-copy}

A ferramenta de cópia de conteúdo do Cloud Manager Adobe permite que os usuários copiem conteúdo mutável sob demanda de ambientes de produção Adobe Experience Manager 6.x hospedados na Managed Services para ambientes inferiores para testes.

## Sobre a cópia de conteúdo {#introduction}

Os dados atuais e reais são valiosos para fins de teste, validação e aceitação do usuário. A ferramenta de cópia de conteúdo permite copiar conteúdo do ambiente de produção do AEM 6.x hospedado no AMS para ambientes de preparo ou de desenvolvimento. Esse fluxo de trabalho permite realizar vários tipos de teste.

Um conjunto de conteúdo define o conteúdo a ser copiado. Um conjunto de conteúdo inclui uma lista de caminhos JCR com o conteúdo mutável a ser copiado. O conteúdo é movido de um ambiente de origem para um ambiente de destino. Tudo isso é feito no mesmo programa do Cloud Manager.

Os seguintes caminhos são permitidos em um conjunto de conteúdo:

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

Ao copiar o conteúdo, o ambiente de origem é a fonte de verdade.

* Quando você edita o conteúdo no ambiente de destino, o conteúdo de origem substitui-o, caso os caminhos correspondam.
* Se os caminhos forem diferentes, o conteúdo da origem será mesclado com o conteúdo do destino.

## Permissões {#permissions}

Para usar a ferramenta de cópia de conteúdo, o usuário deve ter a função de **Gerenciador de implantação** nos ambientes de origem e de destino.

## Criar um conjunto de conteúdo {#create-content-set}

Antes que qualquer conteúdo possa ser copiado, um conjunto de conteúdo deve ser definido. Depois de definidos, os conjuntos de conteúdo podem ser reutilizados para copiar o conteúdo. Siga estas etapas para criar um conjunto de conteúdo.

**Para criar um conjunto de conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, na página **Serviços**, clique em ![Ícone de caixa ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de conteúdo**.

1. Próximo ao canto superior direito da página, clique em **Adicionar conjunto de conteúdo**.

   ![Conjuntos de conteúdo](/help/assets/content-sets.png)

1. Na caixa de diálogo **Adicionar Conjunto de Conteúdo**, na guia **Detalhes**, nos campos **Nome** e **Descrição**, digite um nome e uma descrição opcional para o conjunto de conteúdo e clique em **Continuar**.

   ![Detalhes do conjunto de conteúdo](/help/assets/add-content-set-details.png)

1. Na guia **Caminhos de Conteúdo**, no campo de texto **Caminho**, especifique um caminho para o conteúdo que possa ser alterado e seja incluído no conjunto de conteúdo.

   Somente os caminhos que começam com `/content`, `/conf`, `/etc`, `/var/workflow/models` ou `/var/commerce` estão qualificados para inclusão.

1. Clique em **![Ícone de adição de pasta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) Adicionar caminho** para adicionar (ou incluir) o caminho ao conjunto de conteúdo.

1. (Opcional) Se necessário, adicione caminhos de adição (até 50), conforme necessário, repetindo as duas etapas anteriores. Caso contrário, continue para a próxima etapa.

   ![Adicionar caminhos ao conjunto de conteúdo](/help/assets/add-content-set-paths.png)

1. (Opcional) Para restringir seu conjunto de conteúdo, você pode especificar subcaminhos dentro de um caminho de conteúdo incluído que deve ser excluído.

   1. À direita de um caminho de conteúdo incluído que você deseja restringir, clique em ![Ícone de exclusão de pasta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. No campo de texto, digite um caminho relativo para o caminho raiz visto na caixa de diálogo.
   1. Clique em ![Ícone de exclusão de pasta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **Excluir caminho**.
   1. Se necessário, repita os passos i. a iii. acima para adicionar mais caminhos de exclusão; não há limitação. Caso contrário, continue para a próxima etapa.

   ![Excluir caminhos](/help/assets/add-content-set-paths-excluded.png)

1. (Opcional) Siga qualquer um destes procedimentos:

   1. Clique no ícone ![Cruzar tamanho 500](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) à direita de um subcaminho excluído para excluí-lo.
   1. Clique no ícone ![Mais](https://spectrum.adobe.com/static/icons/ui_18/More.svg) à direita de um caminho de conteúdo incluído e em **Editar** ou **Excluir**.

   ![Editar lista de caminhos](/help/assets/add-content-set-excluded-paths.png)

1. Clique em **Criar**.

Agora você pode usar o conjunto de conteúdo para copiar conteúdo entre ambientes.

## Editar ou excluir um conjunto de conteúdo {#edit-content-set}

Ao editar um conjunto de conteúdo, talvez seja necessário expandir os caminhos configurados para revelar os subcaminhos excluídos.

**Para editar ou excluir um conjunto de conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, em **Serviços**, clique em ![Ícone de caixa ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de conteúdo**.

1. Na tabela da página **Conjuntos de Conteúdo**, clique no ícone ![Mais](https://spectrum.adobe.com/static/icons/ui_18/More.svg) à direita de um caminho de conteúdo incluído e clique em **Editar** ou **Excluir**.

![Editar conjunto de conteúdo](/help/assets/edit-content-set.png)


## Copiar conteúdo {#copy-content}

Após criar um conjunto de conteúdo, você pode usá-lo para copiar o conteúdo.

Um ambiente pode estar indisponível para seleção se qualquer uma das seguintes condições se aplicar:

* O usuário não tem as permissões necessárias.
* No momento, um pipeline ou uma operação de cópia de conteúdo está em execução no ambiente.

**Para copiar o conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, em **Serviços**, clique em ![Ícone de caixa ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de conteúdo**.

1. Na tabela da página **Conjuntos de Conteúdo**, à direita de um caminho de conteúdo incluído que você deseja copiar, clique no ícone ![Mais](https://spectrum.adobe.com/static/icons/ui_18/More.svg) e em **Copiar Conteúdo**.

   ![Cópia de conteúdo](/help/assets/copy-content.png)

1. Na caixa de diálogo **Copiar conteúdo**, selecione o ambiente **Source** e o ambiente **Destino** para sua ação de cópia de conteúdo.

   * As regiões em um ambiente de destino devem ser um subconjunto de regiões em um ambiente de origem.
   * Os problemas de compatibilidade são verificados antes de executar uma ação de cópia de conteúdo. Ao selecionar o ambiente **Destino**, o sistema valida automaticamente os ambientes de origem e destino. Se a validação falhar, o processo será interrompido e uma mensagem de erro será exibida na caixa de diálogo que explica o motivo da falha.

1. (Opcional) Siga qualquer um destes procedimentos:

   1. Para *reter* os caminhos excluídos no Ambiente de destino, verifique **`Do not delete exclude paths from destination`**. Essa configuração mantém intactos os caminhos excluídos especificados no conjunto de conteúdo.
   1. Para *remover* os caminhos excluídos no Ambiente de destino, desmarque **`Do not delete exclude paths from destination`**. Essa configuração exclui os caminhos excluídos especificados no conjunto de conteúdo.
   1. Para copiar o histórico de versões de caminhos do ambiente de origem para o ambiente de destino, marque **Copiar Versões**.

      ![Copiar conteúdo](/help/assets/copying-content.png)

1. Clique em **Copiar**. O status do processo de cópia é exibido no console do conjunto de conteúdo selecionado.

## Monitorar o status da atividade de cópia de conteúdo {#copy-activity}

É possível monitorar o status dos processos de cópia na página **Atividade de cópia de conteúdo**.

**Para monitorar o status da atividade de cópia de conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, em **Serviços**, clique em ![Ícone de histórico ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **Copiar Atividade de Conteúdo**.

   ![Atividade de cópia de conteúdo](/help/assets/copy-content-activity.png)

   Um processo de conteúdo de cópia pode ter um dos seguintes status:

   | Status | Descrição |
   | --- | --- |
   | Em andamento | A operação de cópia de conteúdo está em andamento. |
   | Concluído | A operação de cópia de conteúdo foi concluída com êxito. |
   | Falhou | Falha na operação de cópia de conteúdo. |


## Limitações {#limitations}

A ferramenta de cópia de conteúdo tem as seguintes limitações:

* Não é possível executar a cópia de conteúdo de um ambiente inferior para um superior.
* Só é possível executar a cópia de conteúdo em níveis equivalentes. Ou seja, de autor para autor ou de publicação para publicação.
* Não é possível copiar conteúdo entre programas e entre regiões.
* Só é possível executar uma cópia de conteúdo para uma topologia baseada no armazenamento de dados em nuvem quando os ambientes de origem e destino estão no mesmo provedor de nuvem e na mesma região.
* Não é possível executar operações de cópia de conteúdo simultâneas no mesmo ambiente.
* Não é possível executar a cópia de conteúdo se houver uma operação ativa em execução no ambiente de destino ou de origem, como um pipeline de CI/CD.
* É possível especificar até dez caminhos por conjunto de conteúdo. Não há limitação para os caminhos excluídos.
* A ferramenta de cópia de conteúdo não deve ser usada como uma ferramenta de clonagem ou espelhamento, pois ela não pode rastrear os conteúdos movidos ou excluídos da origem.
* Uma cópia de conteúdo não pode ser pausada ou cancelada depois de iniciada.
* A ferramenta de cópia de conteúdo copia ativos e metadados do Dynamic Media do ambiente superior para o ambiente inferior selecionado. É necessário reprocessar os ativos copiados com o [fluxo de trabalho de processamento de ativos do DAM](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/assets/using/assets-workflow) no ambiente inferior para usar a configuração do Dynamic Media correspondente.
* O processo de cópia de conteúdo é substancialmente mais rápido quando o histórico da versão não é copiado.
* Não há suporte para [configurações do Dynamic Media com ativos maiores que 2 GB habilitados](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb).
* Quando o histórico de versões não é copiado, o processo de cópia de conteúdo é consideravelmente mais rápido.
* As regiões do ambiente de destino devem ser iguais ou um subconjunto das regiões do ambiente de origem.

## Problemas conhecidos {#known-issues}

{{content-copy-known-issues}}
