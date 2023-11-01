---
title: A ferramenta de cópia de conteúdo
description: A ferramenta de cópia de conteúdo do Cloud Manager permite copiar conteúdo mutável sob demanda de seus ambientes de produção do AEM 6.x hospedado no AMS para os ambientes inferiores para fins de teste.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: fe5de4e1ab5cd0d0e317cd399b8e44758a6312c4
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 93%

---


# A ferramenta de cópia de conteúdo {#content-copy}

A ferramenta de cópia de conteúdo do Cloud Manager permite copiar conteúdo mutável sob demanda de seus ambientes de produção do AEM 6.x hospedado no AMS para os ambientes inferiores para fins de teste.

## Introdução {#introduction}

Os dados atuais e reais são valiosos para fins de teste, validação e aceitação do usuário. A ferramenta de cópia de conteúdo permite copiar conteúdo do ambiente de produção do AEM 6.x hospedado no AMS para um ambiente de preparo ou de desenvolvimento para a realização desses testes.

O conteúdo a ser copiado é definido por um conjunto de conteúdo. Um conjunto de conteúdo consiste em uma lista de caminhos JCR que contêm o conteúdo mutável a ser copiado de um ambiente de origem para um ambiente de destino dentro do mesmo programa do Cloud Manager. Os seguintes caminhos são permitidos em um conjunto de conteúdo.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
```

Ao copiar o conteúdo, o ambiente de origem é a fonte de verdade.

* Se o conteúdo tiver sido modificado no ambiente de destino, ele será substituído pelo conteúdo da origem se os caminhos forem os mesmos.
* Se os caminhos forem diferentes, o conteúdo da origem será mesclado ao conteúdo do destino.

>[!NOTE]
>
>Entre em contato com o engenheiro de sucesso do cliente (CSE) para habilitar esse recurso.

## Permissões {#permissions}

Para usar a ferramenta de cópia de conteúdo, o usuário deve ser atribuído à função de **Gerenciador de implantação** nos ambientes de origem e de destino.

## Criação de um conjunto de conteúdo {#create-content-set}

Antes que qualquer conteúdo possa ser copiado, um conjunto de conteúdo deve ser definido. Depois de definidos, os conjuntos de conteúdo podem ser reutilizados para copiar o conteúdo. Siga estas etapas para criar um conjunto de conteúdo.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. Acesse a tela **Ambientes** a partir da página **Visão geral**.

1. Acesse a página **Conjuntos de conteúdo** na tela **Ambientes**.

1. Toque ou clique no botão **Adicionar conjunto de conteúdo** na parte superior direita da tela.

   ![Conjuntos de conteúdo](/help/assets/content-sets.png)

1. Na guia **Detalhes** do assistente, forneça um nome e uma descrição para o conjunto de conteúdo e toque ou clique em **Continuar**.

   ![Detalhes do conjunto de conteúdo](/help/assets/add-content-set-details.png)

1. Na guia **Caminhos de conteúdo** do assistente, especifique os caminhos do conteúdo mutável a ser incluído no conjunto de conteúdo.

   1. Insira o caminho no campo **Adicionar caminho de inclusão**.
   1. Toque ou clique no botão **Adicionar caminho** para adicionar o caminho ao conjunto de conteúdo.
   1. Toque ou clique no botão **Adicionar caminho** novamente, se necessário.

   ![Adicionar caminhos ao conjunto de conteúdo](/help/assets/add-content-set-paths.png)

1. Se você precisar refinar ou restringir o conjunto de conteúdo, os subcaminhos poderão ser excluídos.

   1. Na lista de caminhos incluídos, toque ou clique no ícone **Adicionar subcaminhos de exclusão** ao lado do caminho que deve ser restringido.
   1. Insira o subcaminho a ser excluído abaixo do caminho selecionado.
   1. Toque ou clique em **Excluir caminho**.
   1. Toque ou clique em **Adicionar subcaminhos de exclusão** novamente para adicionar caminhos adicionais a serem excluídos, se necessário.

   ![Excluir caminhos](/help/assets/add-content-set-paths-excluded.png)

1. Você pode modificar os caminhos especificados, se necessário.

   1. Toque ou clique no X ao lado dos subcaminhos excluídos para apagá-los.
   1. Toque ou clique no botão de reticências ao lado dos caminhos para revelar as opções **Editar** e **Excluir**.

   ![Editar lista de caminhos](/help/assets/add-content-set-excluded-paths.png)

1. Toque ou clique em **Criar** para criar o conjunto de conteúdo.

O conjunto de conteúdo agora pode ser usado para copiar conteúdo entre ambientes.

>[!NOTE]
>
>Você pode adicionar até 50 caminhos em um conjunto de conteúdo.
>Não há limitação de caminhos excluídos.

## Editar um conjunto de conteúdo {#edit-content-set}

Para esse processo, as etapas são semelhantes às da criação de conteúdo. Porém, em vez de tocar ou clicar em **Adicionar conjunto de conteúdo**, selecione um conjunto existente no console e clique em **Editar** no menu de reticências.

![Editar conjunto de conteúdo](/help/assets/edit-content-set.png)

Ao editar seu conjunto de conteúdo, talvez seja necessário expandir os caminhos configurados para revelar os subcaminhos excluídos.

## Copiar conteúdo {#copy-content}

Depois que um conjunto de conteúdo é criado, você pode usá-lo para copiar conteúdo. Siga estas etapas para copiar conteúdo.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. Acesse a tela **Ambientes** a partir da página **Visão geral**.

1. Acesse a página **Conjuntos de conteúdo** na tela **Ambientes**.

1. Selecione um conjunto de conteúdo no console e clique em **Copiar conteúdo** no menu de reticências.

   ![Cópia de conteúdo](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Um ambiente pode não ser selecionável se:
   >
   >* O usuário não tiver as permissões apropriadas.
   >* O ambiente tiver um pipeline em execução ou uma operação de cópia de conteúdo em andamento.

1. Na caixa de diálogo **Copiar conteúdo**, especifique a origem e o destino da sua ação de cópia de conteúdo.

1. Você pode optar por excluir ou manter os caminhos de exclusão no ambiente de destino. Selecione a caixa de seleção `Do not delete exclude paths from destination` se desejar manter os caminhos de exclusão especificados no conjunto de conteúdo. Se a caixa de seleção estiver desmarcada, os caminhos de exclusão serão excluídos no ambiente de destino.

1. Você pode optar por copiar o histórico de versões dos caminhos que estão sendo copiados do ambiente de origem para o de destino. Marcar caixa de seleção `Copy Versions` se desejar copiar todos os históricos de versão.

   ![Copiar conteúdo](/help/assets/copying-content.png)

1. Toque ou clique em **Copiar**.

O processo de cópia será iniciado. O status do processo de cópia é exibido no console do conjunto de conteúdo selecionado.

## Atividade de cópia de conteúdo {#copy-activity}

Você pode monitorar o status dos processos de cópia na página **Atividade de cópia de conteúdo**.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. Acesse a tela **Ambientes** a partir da página **Visão geral**.

1. Acesse a página **Atividade de cópia de conteúdo** na tela **Ambientes**.

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

* Uma cópia de conteúdo não pode ser executada de um ambiente inferior para um superior.
* A cópia de conteúdo só pode ser executada no mesmo nível (ou seja, de autor para autor ou publicação para publicação).
* Não é possível copiar conteúdo entre programas e entre regiões.
* A cópia de conteúdo para a topologia baseada no armazenamento de dados em nuvem só pode ser executada quando os ambientes de origem e de destino estão no mesmo provedor de nuvem e na mesma região.
* Não é possível executar operações de cópia de conteúdo simultâneas no mesmo ambiente.
* A cópia de conteúdo não pode ser executada se houver uma operação ativa em execução no ambiente de destino ou de origem, como um pipeline de CI/CD.
* É possível especificar até dez caminhos por conjunto de conteúdo. Não há limitação de caminhos excluídos.
* A ferramenta de cópia de conteúdo não deve ser usada como uma ferramenta de clonagem ou espelhamento, pois ela não pode rastrear os conteúdos movidos ou excluídos da origem.
* Uma cópia de conteúdo não pode ser pausada ou cancelada depois de iniciada.
* A ferramenta de cópia de conteúdo copia ativos juntamente com metadados relacionados à mídia dinâmica do ambiente superior para o ambiente inferior selecionado.
   * Os ativos copiados precisam ser reprocessados usando o [Fluxo de trabalho dos ativos do processo DAM](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-workflow.html?lang=pt-BR) no ambiente inferior para usar a respectiva configuração de mídia dinâmica.
* O processo de cópia de conteúdo será substancialmente mais rápido quando o histórico da versão não for copiado.
