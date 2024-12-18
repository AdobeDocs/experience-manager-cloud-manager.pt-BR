---
title: Cópia de conteúdo para consistência do ambiente
description: A Cópia de conteúdo no Cloud Manager permite que os usuários copiem conteúdo mutável sob demanda de ambientes de produção do Adobe Experience Manager 6.x hospedados no Adobe Managed Services para ambientes inferiores para fins de teste.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: e3a656605ac59ca1f95985426932fddf2b53b7c9
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 98%

---


# Cópia de conteúdo para consistência do ambiente {#content-copy}

A Cópia de conteúdo no Cloud Manager permite que os usuários copiem conteúdo mutável sob demanda de ambientes de produção do Adobe Experience Manager 6.x hospedados no Adobe Managed Services para ambientes inferiores para fins de teste.

## Sobre cópia de conteúdo {#introduction}

Os dados atuais e reais são valiosos para fins de teste, validação e aceitação do usuário. A Cópia de conteúdo permite que você copie conteúdo do seu ambiente de produção AEM 6.x hospedado no AMS para ambientes de preparação ou desenvolvimento. Esse fluxo de trabalho permite realizar vários tipos de teste.

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

Quando você edita o conteúdo no ambiente de destino, o conteúdo de origem substitui-o, caso os caminhos correspondam.

Se os caminhos forem diferentes, o conteúdo da origem será mesclado com o conteúdo do destino.

### Permissões {#permissions}

Para usar o recurso Cópia de conteúdo, o usuário deve ser atribuído à função **Gerente de implantação** nos ambientes de origem e de destino.

## Criar um conjunto de conteúdo {#create-content-set}

Antes que qualquer conteúdo possa ser copiado, um conjunto de conteúdo deve ser definido. Depois de definidos, os conjuntos de conteúdo podem ser reutilizados para copiar o conteúdo. Siga estas etapas para criar um conjunto de conteúdo.

**Para criar um conjunto de conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, na página **Serviços**, clique em ![Ícone de caixa ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de conteúdo**.

1. Próximo ao canto superior direito da página, clique em **Adicionar conjunto de conteúdo**.

   ![Conjuntos de conteúdo](/help/assets/content-sets.png)

1. Na caixa de diálogo **`Add Content Set`**, na guia **Detalhes**, nos campos **Nome** e **Descrição**, digite um nome e uma descrição opcional para o conjunto de conteúdo e clique em **Continuar**.

   ![Detalhes do conjunto de conteúdo](/help/assets/add-content-set-details.png)

1. Na guia **Caminhos de conteúdo**, no campo de texto **Caminho**, especifique um caminho para o conteúdo que possa ser alterado e incluído no conjunto de conteúdo.

   Somente os caminhos que começam com `/content`, `/conf`, `/etc`, `/var/workflow/models` ou `/var/commerce` podem ser incluídos.

1. Clique no **![Ícone de adição de pasta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) Adicionar caminho** para adicionar (ou incluir) o caminho para o conjunto de conteúdo.

1. (Opcional) Se necessário, adicione caminhos de adição (até 50), conforme necessário, repetindo as duas etapas anteriores. Caso contrário, continue para a próxima etapa.

   ![Adicionar caminhos ao conjunto de conteúdo](/help/assets/add-content-set-paths.png)

1. (Opcional) Para restringir seu conjunto de conteúdo, é possível especificar subcaminhos em um caminho de conteúdo incluído que deve ser excluído.

   1. À direita de um caminho de conteúdo incluído que você deseja restringir, clique no ![Ícone de apagar pasta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. No campo de texto, digite um caminho relativo ao caminho raiz visto na caixa de diálogo.
   1. Clique no ![Ícone de apagar pasta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **Excluir caminho**.
   1. Se necessário, repita as etapas i. a iii. acima para adicionar mais caminhos de exclusão; não há limitação. Caso contrário, continue para a próxima etapa.

   ![Excluir caminhos](/help/assets/add-content-set-paths-excluded.png)

1. (Opcional) Siga qualquer um destes procedimentos:

   1. Clique no ícone de ![X tamanho 500](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) à direita de um subcaminho excluído para apagá-lo.
   1. Clique no ícone de ![Mais](https://spectrum.adobe.com/static/icons/ui_18/More.svg) à direita de um caminho de conteúdo incluído e em **Editar** ou **Excluir**.

   ![Editar lista de caminhos](/help/assets/add-content-set-excluded-paths.png)

1. Clique em **Criar**. Agora você pode usar o conjunto de conteúdo para copiar conteúdo entre ambientes.

## Editar ou apagar um conjunto de conteúdo {#edit-content-set}

Ao editar seu conjunto de conteúdo, talvez seja necessário expandir os caminhos configurados para revelar os subcaminhos excluídos.

**Para editar ou apagar um conjunto de conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, em **Serviços**, clique em ![Ícone de caixa ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de conteúdo**.

1. Na tabela da página **Conjuntos de conteúdo**, clique no ícone de ![Mais](https://spectrum.adobe.com/static/icons/ui_18/More.svg) à direita de um caminho de conteúdo incluído e clique em **Editar** ou **Excluir**.

![Editar conjunto de conteúdo](/help/assets/edit-content-set.png)

## Copiar conteúdo {#copy-content}

Depois que um conjunto de conteúdo é criado, você pode usá-lo para copiar conteúdo. 

Um ambiente pode estar indisponível para seleção se qualquer uma das seguintes condições se aplicar:

* O usuário não tem as permissões necessárias.
* No momento, um pipeline ou uma operação de cópia de conteúdo está em execução no ambiente.

**Para copiar conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, em **Serviços**, clique em ![Ícone de caixa ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de conteúdo**.

1. Na tabela da página **Conjuntos de conteúdo**, à direita de um caminho de conteúdo incluído que você deseja copiar, clique no ícone ![Mais](https://spectrum.adobe.com/static/icons/ui_18/More.svg) e em **Copiar conteúdo**.

   ![Cópia de conteúdo](/help/assets/copy-content.png)

1. Na caixa de diálogo **Copiar conteúdo**, selecione o ambiente de **Origem** e o ambiente de **Destino** para sua ação de cópia de conteúdo.

   * As regiões em um ambiente de destino devem ser um subconjunto das regiões em um ambiente de origem.
   * Os problemas de compatibilidade são verificados antes de executar uma ação de cópia de conteúdo. Ao selecionar o ambiente de **Destino**, o sistema valida automaticamente os ambientes de origem e destino. Se a validação falhar, o processo será interrompido e uma mensagem de erro será exibida na caixa de diálogo que explica o motivo da falha.

     ![Copiar conteúdo](/help/assets/copying-content.png)

1. (Opcional) Siga um destes procedimentos:

   1. Para *reter* os caminhos excluídos no ambiente de destino, marque **`Do not delete exclude paths from destination`**. Essa configuração mantém intactos os caminhos excluídos especificados no conjunto de conteúdo.
   1. Para *remover* os caminhos excluídos no ambiente de destino, desmarque **`Do not delete exclude paths from destination`**. Essa configuração apaga os caminhos excluídos especificados no conjunto de conteúdo.
   1. Para copiar o histórico de versões de caminhos do ambiente de origem para o ambiente de destino, marque **Copiar versões**. O processo de cópia de conteúdo é muito mais rápido quando o histórico da versão *não* é copiado.

1. Clique em **Copiar**. O status do processo de cópia é exibido no console do conjunto de conteúdo selecionado.

## Verificar o status de uma cópia de conteúdo {#copy-activity}

É possível monitorar o status dos processos de cópia na página **Atividade de cópia de conteúdo**.

**Para verificar o status de uma cópia de conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, em **Serviços**, clique no ![Ícone de Histórico ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **Atividade de cópia de conteúdo**.

   ![Atividade de cópia de conteúdo](/help/assets/copy-content-activity.png)

   Um processo de cópia de conteúdo pode ter um dos seguintes status:

   | Status | Descrição |
   | --- | --- |
   | Em andamento | O processo de cópia de conteúdo está em andamento. |
   | Concluída | O processo de cópia de conteúdo foi concluído com êxito. |
   | Falhou | Falha no processo de cópia de conteúdo. |

## Limitações da cópia de conteúdo {#limitations}

* Não é possível executar a cópia de conteúdo de um ambiente inferior para um superior.
* Só é possível executar a cópia de conteúdo em níveis equivalentes. Ou seja, de autor para autor ou de publicação para publicação.
* Não é possível copiar conteúdo entre programas e entre regiões.
* Só é possível executar uma cópia de conteúdo para uma topologia baseada no armazenamento de dados em nuvem quando os ambientes de origem e destino estão no mesmo provedor de nuvem e na mesma região.
* Não é possível executar operações de cópia de conteúdo simultâneas no mesmo ambiente.
* Não é possível executar a cópia de conteúdo se houver uma operação ativa em execução no ambiente de destino ou de origem, como um pipeline de CI/CD.
* A cópia de conteúdo não deve ser usada como uma ferramenta de clonagem ou espelhamento porque não pode rastrear conteúdos movidos ou excluídos na origem.
* Uma cópia de conteúdo não pode ser pausada ou cancelada depois de iniciada.
* A cópia de conteúdo duplica ativos e metadados do Dynamic Media do ambiente superior para o ambiente inferior selecionado. É necessário reprocessar os ativos copiados com o [fluxo de trabalho de processamento de ativos do DAM](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/assets/using/assets-workflow) no ambiente inferior para usar a configuração do Dynamic Media correspondente.
* [Configurações do Dynamic Media com ativos maiores que 2 GB habilitados](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) não são compatíveis.
* As regiões do ambiente de destino devem ser iguais às regiões do ambiente de origem, ou um subconjunto delas.

## Problemas conhecidos da Cópia de conteúdo {#known-issues}

{{content-copy-known-issues}}
