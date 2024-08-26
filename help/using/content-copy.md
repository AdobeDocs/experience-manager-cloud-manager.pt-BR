---
title: A ferramenta de cópia de conteúdo
description: A ferramenta de cópia de conteúdo do Cloud Manager permite copiar conteúdo mutável sob demanda dos ambientes de produção do AEM 6.x hospedado no AMS aos ambientes inferiores para fins de teste.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 90%

---


# A ferramenta de cópia de conteúdo {#content-copy}

A ferramenta de cópia de conteúdo do Cloud Manager permite copiar conteúdo mutável sob demanda dos ambientes de produção do AEM 6.x hospedado no AMS aos ambientes inferiores para fins de teste.

## Introdução {#introduction}

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

## Criação de um conjunto de conteúdo {#create-content-set}

Antes que qualquer conteúdo possa ser copiado, um conjunto de conteúdo deve ser definido. Depois de definidos, os conjuntos de conteúdo podem ser reutilizados para copiar o conteúdo. Siga estas etapas para criar um conjunto de conteúdo.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Na página **Visão geral**, navegue até a tela **Ambientes**.

1. Na tela **Ambientes**, navegue até a página **Conjuntos de conteúdo**.

1. Próximo ao canto superior direito da tela, clique em **Adicionar conjunto de conteúdo**.

   ![Conjuntos de conteúdo](/help/assets/content-sets.png)

1. Na guia **Detalhes** do assistente, forneça um nome e uma descrição para o conjunto de conteúdo, e clique em **Continuar**.

   ![Detalhes do conjunto de conteúdo](/help/assets/add-content-set-details.png)

1. Na guia **Caminhos de conteúdo** do assistente, especifique os caminhos do conteúdo mutável a ser incluído no conjunto de conteúdo.

   1. Insira o caminho no campo **Adicionar caminho de inclusão**.
   1. Clique no botão **Adicionar caminho** para adicionar o caminho ao conjunto de conteúdo.
   1. Clique em **Adicionar caminho** novamente, se necessário.

   ![Adicionar caminhos ao conjunto de conteúdo](/help/assets/add-content-set-paths.png)

1. Se você precisar refinar ou restringir o conjunto de conteúdo, os subcaminhos poderão ser excluídos.

   1. Na lista de caminhos inclusos, clique no ícone **Adicionar subcaminhos de exclusão** ao lado do caminho que você precisa restringir.
   1. Insira o subcaminho a ser excluído a partir do caminho selecionado.
   1. Clique em **Excluir caminho**.
   1. Novamente, clique em **Adicionar subcaminhos de exclusão** para adicionar caminhos a serem excluídos, se necessário.

   ![Excluir caminhos](/help/assets/add-content-set-paths-excluded.png)

1. Você pode modificar os caminhos especificados, se necessário.

   1. Clique em `X` ao lado dos subcaminhos excluídos para excluí-los.
   1. Clique no botão de reticências ao lado dos caminhos para revelar as opções **Editar** e **Excluir**.

   ![Editar lista de caminhos](/help/assets/add-content-set-excluded-paths.png)

1. Clique em **Criar** para criar o conjunto de conteúdo.

O conjunto de conteúdo agora pode ser usado para copiar conteúdo entre ambientes.

>[!NOTE]
>
>Você pode adicionar até 50 caminhos em um conjunto de conteúdo.
>Não há limitação para os caminhos excluídos.

## Editar um conjunto de conteúdo {#edit-content-set}

Para esse processo, as etapas são semelhantes às da criação de conteúdo. Porém, em vez de clicar em **Adicionar conjunto de conteúdo**, selecione um conjunto existente no console e clique em **Editar** no menu de reticências.

![Editar conjunto de conteúdo](/help/assets/edit-content-set.png)

Ao editar seu conjunto de conteúdo, talvez seja necessário expandir os caminhos configurados para revelar os subcaminhos excluídos.

## Copiar conteúdo {#copy-content}

Depois que um conjunto de conteúdo é criado, você pode usá-lo para copiar conteúdo. Siga estas etapas para copiar conteúdo.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Na página **Visão geral**, navegue até a tela **Ambientes**.

1. Na tela **Ambientes**, navegue até a página **Conjuntos de conteúdo**.

1. Selecione um conjunto de conteúdo no console e clique em **Copiar conteúdo** no menu de reticências.

   ![Cópia de conteúdo](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Um ambiente pode não ser selecionável se:
   >
   >* O usuário não tiver as permissões apropriadas.
   >* O ambiente tiver um pipeline em execução ou uma operação de cópia de conteúdo em andamento.

1. Na caixa de diálogo **Copiar conteúdo**, especifique os ambientes de origem e destino para sua ação de cópia de conteúdo.
   * As regiões do ambiente de destino devem ser iguais ou um subconjunto das regiões do ambiente de origem.

1. Você pode optar por apagar ou manter os caminhos de exclusão no ambiente de destino. Marque a caixa de seleção `Do not delete exclude paths from destination` para reter `exclude paths`, conforme especificado no conjunto de conteúdo. Se a caixa de seleção estiver desmarcada, os caminhos de exclusão serão excluídos no ambiente de destino.

1. É possível optar por copiar o histórico de versões dos caminhos que estão sendo copiados do ambiente de origem para o de destino. Marque a caixa de seleção `Copy Versions` se quiser copiar todos os históricos de versões.

   ![Copiar conteúdo](/help/assets/copying-content.png)

1. Clique em **Copiar**.

O processo de cópia será iniciado. O status do processo de cópia é exibido no console do conjunto de conteúdo selecionado.

## Atividade de cópia de conteúdo {#copy-activity}

É possível monitorar o status dos processos de cópia na página **Atividade de cópia de conteúdo**.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Na página **Visão geral**, navegue até a tela **Ambientes**.

1. Na tela **Ambientes**, navegue até a página **Atividade de cópia de conteúdo**.

![Atividade de cópia de conteúdo](/help/assets/copy-content-activity.png)

### Status da cópia de conteúdo {#statuses}

Depois de começar a copiar o conteúdo, o processo poderá ter um dos status a seguir.

| Status | Descrição |
|---|---|
| Em andamento | A operação de cópia de conteúdo está em andamento |
| Falhou | A operação de cópia de conteúdo falhou |
| Concluído | A operação de cópia de conteúdo foi concluída com sucesso |

## Limitações {#limitations}

A ferramenta de cópia de conteúdo tem as seguintes limitações.

* Não é possível executar a cópia de conteúdo de um ambiente inferior para um superior.
* Só é possível executar a cópia de conteúdo em níveis equivalentes. Ou seja, de autor para autor ou de publicação para publicação.
* Não é possível copiar conteúdo entre programas e entre regiões.
* Só é possível executar uma cópia de conteúdo para uma topologia baseada no armazenamento de dados em nuvem quando os ambientes de origem e destino estão no mesmo provedor de nuvem e na mesma região.
* Não é possível executar operações de cópia de conteúdo simultâneas no mesmo ambiente.
* Não é possível executar a cópia de conteúdo se houver uma operação ativa em execução no ambiente de destino ou de origem, como um pipeline de CI/CD.
* É possível especificar até dez caminhos por conjunto de conteúdo. Não há limitação para os caminhos excluídos.
* A ferramenta de cópia de conteúdo não deve ser usada como uma ferramenta de clonagem ou espelhamento, pois ela não pode rastrear os conteúdos movidos ou excluídos da origem.
* Uma cópia de conteúdo não pode ser pausada ou cancelada depois de iniciada.
* A ferramenta de cópia de conteúdo copia ativos e metadados Dynamic Media do ambiente superior para o ambiente inferior selecionado. É necessário reprocessar os ativos copiados com o [fluxo de trabalho de processamento de ativos do DAM](https://experienceleague.adobe.com/br/docs/experience-manager-65/content/assets/using/assets-workflow) no ambiente inferior para usar a configuração de mídia dinâmica correspondente.
* O processo de cópia de conteúdo é substancialmente mais rápido quando o histórico da versão não é copiado.
* [Não há suporte para configurações do Dynamic Media com ativos maiores que 2 GB habilitados](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb).
* Quando o histórico de versões não é copiado, o processo de cópia de conteúdo é consideravelmente mais rápido.
* As regiões do ambiente de destino devem ser iguais ou um subconjunto das regiões do ambiente de origem.

## Problemas conhecidos {#known-issues}

{{content-copy-known-issues}}
