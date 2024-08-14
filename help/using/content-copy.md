---
title: A ferramenta de cópia de conteúdo
description: A ferramenta de cópia de conteúdo do Cloud Manager permite que os usuários copiem conteúdo mutável sob demanda de ambientes de produção AEM 6.x hospedados no AMS para ambientes mais baixos para testes.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 2563c58431e58d2fc5917a2ad88835bbdd4224f2
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 42%

---


# A ferramenta de cópia de conteúdo {#content-copy}

A ferramenta de cópia de conteúdo do Cloud Manager permite que os usuários copiem conteúdo mutável sob demanda de ambientes de produção AEM 6.x hospedados no AMS para ambientes mais baixos para testes.

## Introdução {#introduction}

Os dados atuais e reais são valiosos para fins de teste, validação e aceitação do usuário. A ferramenta de cópia de conteúdo permite copiar o conteúdo do ambiente de produção do AEM 6.x hospedado no AMS para ambientes de preparo ou desenvolvimento. Esse fluxo de trabalho suporta vários cenários de teste.

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

* Se você editar o conteúdo no ambiente de destino, o conteúdo de origem o substituirá se os caminhos corresponderem.
* Se os caminhos forem diferentes, o conteúdo da origem será mesclado com o conteúdo no destino.

## Permissões {#permissions}

Para usar a ferramenta de cópia de conteúdo, o usuário deve ser atribuído à função de **Gerente de Implantação** nos ambientes de origem e destino.

## Criação de um conjunto de conteúdo {#create-content-set}

Antes que qualquer conteúdo possa ser copiado, um conjunto de conteúdo deve ser definido. Depois de definidos, os conjuntos de conteúdo podem ser reutilizados para copiar o conteúdo. Siga estas etapas para criar um conjunto de conteúdo.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Na página **Visão geral**, navegue até a tela **Ambientes**.

1. Na tela **Ambientes**, navegue até a página **Conjuntos de conteúdo**.

1. Próximo ao canto superior direito da tela, clique em **Adicionar conjunto de conteúdo**.

   ![Conjuntos de conteúdo](/help/assets/content-sets.png)

1. Na guia **Detalhes** do assistente, forneça um nome e uma descrição para o conjunto de conteúdo e clique em **Continuar**.

   ![Detalhes do conjunto de conteúdo](/help/assets/add-content-set-details.png)

1. Na guia **Caminhos de conteúdo** do assistente, especifique os caminhos do conteúdo mutável a ser incluído no conjunto de conteúdo.

   1. Insira o caminho no campo **Adicionar caminho de inclusão**.
   1. Clique em **Adicionar caminho** para adicionar o caminho ao conjunto de conteúdo.
   1. Clique em **Adicionar caminho** novamente, conforme necessário.

   ![Adicionar caminhos ao conjunto de conteúdo](/help/assets/add-content-set-paths.png)

1. Se você precisar refinar ou restringir o conjunto de conteúdo, os subcaminhos poderão ser excluídos.

   1. Na lista de caminhos incluídos, clique no ícone **Adicionar/excluir subcaminhos** ao lado do caminho que você precisa restringir.
   1. Insira o subcaminho a ser excluído do caminho selecionado.
   1. Clique em **Excluir Caminho**.
   1. Novamente, clique em **Adicionar subcaminhos de exclusão** para adicionar outros caminhos a serem excluídos conforme necessário.

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
>Não há limitação de caminhos excluídos.

## Edição de um conjunto de conteúdo {#edit-content-set}

Para esse processo, as etapas são semelhantes às da criação de conteúdo. Em vez de clicar em **Adicionar conjunto de conteúdo**, selecione um conjunto existente no console e selecione **Editar** no menu de reticências.

![Editar conjunto de conteúdo](/help/assets/edit-content-set.png)

Ao editar seu conjunto de conteúdo, talvez seja necessário expandir os caminhos configurados para revelar os subcaminhos excluídos.

## Como copiar conteúdo {#copy-content}

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

1. Você pode optar por excluir ou manter os caminhos de exclusão no ambiente de destino. Marque a caixa de seleção `Do not delete exclude paths from destination` para reter `exclude paths` especificados no conjunto de conteúdo. Se a caixa de seleção estiver desmarcada, os caminhos de exclusão serão excluídos no ambiente de destino.

1. Você pode optar por copiar o histórico de versões dos caminhos que estão sendo copiados do ambiente de origem para o de destino. Marque a caixa de seleção `Copy Versions` se desejar copiar todos os históricos de versão.

   ![Copiar conteúdo](/help/assets/copying-content.png)

1. Clique em **Copiar**.

O processo de cópia será iniciado. O status do processo de cópia é exibido no console do conjunto de conteúdo selecionado.

## Atividade de cópia de conteúdo {#copy-activity}

Você pode monitorar o status dos processos de cópia na página **Atividade de cópia de conteúdo**.

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

* Uma cópia de conteúdo não pode ser executada de um ambiente inferior para um ambiente superior.
* A cópia de conteúdo só pode ser executada na mesma camada. Ou seja, autor-autor ou publicação-publicação.
* Não é possível copiar conteúdo entre programas e entre regiões.
* A cópia de conteúdo para a topologia baseada no armazenamento de dados em nuvem só pode ser executada quando os ambientes de origem e de destino estão no mesmo provedor de nuvem e na mesma região.
* Não é possível executar operações simultâneas de cópia de conteúdo no mesmo ambiente.
* A cópia do conteúdo não pode ser executada se houver alguma operação ativa em execução no ambiente de destino ou de origem, como um pipeline de CI/CD.
* É possível especificar até dez caminhos por conjunto de conteúdo. Não há limitação de caminhos excluídos.
* A ferramenta de cópia de conteúdo não deve ser usada como uma ferramenta de clonagem ou espelhamento, pois ela não pode rastrear os conteúdos movidos ou excluídos da origem.
* Uma cópia de conteúdo não pode ser pausada ou cancelada depois de iniciada.
* A ferramenta de cópia de conteúdo copia ativos juntamente com metadados relacionados à mídia dinâmica do ambiente superior para o ambiente inferior selecionado.
   * Os ativos copiados precisam ser reprocessados usando o [Fluxo de trabalho dos ativos do processo DAM](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-workflow.html?lang=pt-BR) no ambiente inferior para usar a respectiva configuração de mídia dinâmica.
* O processo de cópia de conteúdo será substancialmente mais rápido quando o histórico de versão não for copiado.
* [Não há suporte para configurações do Dynamic Media com ativos maiores que 2 GB habilitados](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb).
* Quando o histórico de versões não é copiado, o processo de cópia de conteúdo é substancialmente mais rápido.
* As regiões do ambiente de destino devem ser iguais ou um subconjunto das regiões do ambiente de origem.

## Problemas conhecidos {#known-issues}

{{content-copy-known-issues}}
