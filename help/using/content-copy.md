---
title: A ferramenta Cópia de conteúdo
description: A ferramenta de cópia de conteúdo do Cloud Manager permite que os usuários copiem conteúdo mutável sob demanda de seus ambientes de produção de AEM para ambientes inferiores para fins de teste.
source-git-commit: e32e51f7d10e753b7ecb2a63adb36d1b6c90fcc1
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 8%

---


# A ferramenta Cópia de conteúdo {#content-copy}

A ferramenta de cópia de conteúdo do Cloud Manager permite que os usuários copiem conteúdo mutável sob demanda de seus ambientes de produção de AEM para ambientes inferiores para fins de teste.

## Introdução {#introduction}

Os dados atuais e reais são valiosos para fins de teste, validação e aceitação do usuário. A ferramenta de cópia de conteúdo permite copiar o conteúdo do ambiente de AEM de produção para um ambiente de preparo ou desenvolvimento para esse teste.

O conteúdo a ser copiado é definido por um conjunto de conteúdo. Um conjunto de conteúdo consiste em uma lista de caminhos JCR que contêm o conteúdo mutável a ser copiado de um ambiente de origem para um ambiente de destino no mesmo programa do Cloud Manager. Os seguintes caminhos são permitidos em um conjunto de conteúdo.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
```

Ao copiar o conteúdo, o ambiente de origem é a fonte de verdade.

* Se o conteúdo tiver sido modificado no ambiente de destino, ele será substituído pelo conteúdo na origem, se os caminhos forem os mesmos.
* Se os caminhos forem diferentes, o conteúdo da origem será unido ao conteúdo no destino.

## Permissões {#permissions}

Para usar a ferramenta de cópia de conteúdo, determinadas permissões são necessárias nos ambientes de origem e de destino.

| Recurso de cópia de conteúdo | No AEM Administrador Group? | Na Função do Gerenciador de Implantação? |
|---|---|---|
| Criar e modificar [conjuntos de conteúdo](#create-content-set) | Sim | Não |
| Inicie ou cancele o [processo de cópia de conteúdo](#copy-content) | Sim | Sim |

## Criar um conjunto de conteúdo {#create-content-set}

Antes que qualquer conteúdo possa ser copiado, um conjunto de conteúdo deve ser definido. Depois de definido, os conjuntos de conteúdo podem ser reutilizados para copiar o conteúdo. Siga estas etapas para criar um conjunto de conteúdo.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. Acesse a tela **Ambientes** a partir da página **Visão geral**.

1. Navegue até o **Conjuntos de conteúdo** da página **Ambientes** tela.

1. Toque ou clique no botão **Adicionar conjunto de conteúdo** na parte superior direita da tela.

   ![Conjuntos de conteúdo](/help/assets/content-sets.png)

1. No **Detalhes** guia do assistente, forneça um nome e uma descrição para o conjunto de conteúdo e toque ou clique em **Continuar**.

   ![Detalhes do conjunto de conteúdo](/help/assets/add-content-set-details.png)

1. No **Caminhos de conteúdo** do assistente, especifique os caminhos do conteúdo mutável a ser incluído no conjunto de conteúdo.

   1. Insira o caminho no **Adicionar caminho Incluir** campo.
   1. Toque ou clique no botão **Adicionar caminho** para adicionar o caminho ao conjunto de conteúdo.
   1. Toque ou clique no botão **Adicionar caminho** novamente, conforme necessário.

   ![Adicionar caminhos ao conjunto de conteúdo](/help/assets/add-content-set-paths.png)

1. Se você precisar refinar ou restringir o conjunto de conteúdo, os subcaminhos poderão ser excluídos.

   1. Na lista de caminhos incluídos, toque ou clique no botão **Adicionar subcaminhos excluídos** ícone ao lado do caminho que deve ser restringido.
   1. Insira o subcaminho a ser excluído abaixo do caminho selecionado.
   1. Toque ou clique **Excluir caminho**.
   1. Toque ou clique **Adicionar subcaminhos excluídos** novamente para adicionar caminhos adicionais a serem excluídos, conforme necessário.

   ![Excluir caminhos](/help/assets/add-content-set-paths-excluded.png)

1. Você pode modificar os caminhos especificados, se necessário.

   1. Toque ou clique no X ao lado dos subcaminhos excluídos para excluí-los.
   1. Toque ou clique no botão reticências ao lado de caminhos para revelar **Editar** e **Excluir** opções.

   ![Editar lista de caminhos](/help/assets/add-content-set-excluded-paths.png)

1. Toque ou clique **Criar** para criar o conjunto de conteúdo.

O conjunto de conteúdo agora pode ser usado para copiar conteúdo entre ambientes.

## Editar um conjunto de conteúdo {#edit-content-set}

Siga etapas semelhantes ao criar uma etapa de conteúdo. Em vez de tocar ou clicar em **Adicionar conjunto de conteúdo**, selecione um conjunto existente no console e selecione **Editar** no menu reticências.

![Editar conjunto de conteúdo](/help/assets/edit-content-set.png)

Ao editar seu conjunto de conteúdo, talvez seja necessário expandir os caminhos configurados para revelar os subcaminhos excluídos.

## Copiar conteúdo {#copy-content}

Depois que um conjunto de conteúdo é criado, você pode usá-lo para copiar o conteúdo. Siga estas etapas para copiar conteúdo.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. Acesse a tela **Ambientes** a partir da página **Visão geral**.

1. Navegue até o **Conjuntos de conteúdo** da página **Ambientes** tela.

1. Selecione um conjunto de conteúdo no console e selecione **Copiar conteúdo** no menu reticências.

   ![Cópia de conteúdo](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Um ambiente não pode ser selecionado se:
   >
   >* O usuário não tem as permissões apropriadas.
   >* O ambiente tem um pipeline em execução ou uma operação de cópia de conteúdo em andamento.


1. No **Copiar conteúdo** , especifique a origem e o destino da sua ação de cópia de conteúdo.

   ![Como copiar conteúdo](/help/assets/copying-content.png)

1. Toque ou clique **Copiar**.

O processo de cópia é iniciado. O status do processo de cópia é refletido no console do conjunto de conteúdo selecionado.

## Atividade de cópia de conteúdo {#copy-activity}

Você pode monitorar o status dos processos de cópia na **Atividade Copiar conteúdo** página.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriado.

1. Acesse a tela **Ambientes** a partir da página **Visão geral**.

1. Navegue até o **Atividade Copiar conteúdo** da página **Ambientes** tela.

![Atividade de cópia de conteúdo](/help/assets/copy-content-activity.png)

### Status da cópia de conteúdo {#statuses}

Depois de começar a copiar o conteúdo, o processo poderá ter um dos status a seguir.

| Status | Descrição |
|---|---|
| Em andamento | Operação de cópia de conteúdo em andamento |
| Falhou | Falha na operação de cópia de conteúdo |
| Concluído | Operação de cópia de conteúdo concluída com êxito |

## Limitações {#limitations}

A ferramenta de cópia de conteúdo tem as seguintes limitações.

* Uma cópia de conteúdo não pode ser executada de um ambiente inferior para um ambiente superior.
* A cópia de conteúdo só pode ser executada no mesmo nível (ou seja, autor-autor ou publicação-publicação).
* Não é possível copiar conteúdo entre programas.
* Não é possível executar operações de cópia de conteúdo simultâneo no mesmo ambiente.
* A cópia de conteúdo não pode ser executada se houver uma operação ativa em execução no ambiente de destino ou de origem, como um pipeline de CI/CD.
* É possível especificar até dez caminhos por conjunto de conteúdo. Não há limitação em caminhos excluídos.
* A ferramenta de cópia de conteúdo não deve ser usada como uma ferramenta de clonagem ou espelhamento, pois não pode rastrear o conteúdo movido ou excluído na origem.
* A ferramenta de cópia de conteúdo não tem nenhum recurso de controle de versão e não pode detectar automaticamente o conteúdo modificado ou o conteúdo recém-criado no ambiente de origem em um conjunto de conteúdo desde a última operação de cópia de conteúdo.
   * Se quiser atualizar seu ambiente de destino com alterações de conteúdo somente desde a última operação de cópia de conteúdo, será necessário criar um conjunto de conteúdo. Nesse conjunto, especifique os caminhos na instância de origem onde as alterações foram feitas desde a última operação de cópia de conteúdo.
* As informações de versão não estão incluídas em uma cópia de conteúdo.
