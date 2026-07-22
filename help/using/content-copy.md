---
title: Cópia de conteúdo para consistência do ambiente
description: A Cópia de conteúdo no Cloud Manager permite que os usuários copiem conteúdo mutável sob demanda de ambientes de produção do Adobe Experience Manager 6.x hospedados no Adobe Managed Services para ambientes inferiores para fins de teste.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
TQID: https://experienceleague.adobe.com/ffcf9UNSOp7oIpDZdtLcoFWp-Ww-A1XV3kCDmKqJLSw
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 845c182685d59844a2349c90d176d3e7c8a594cf
workflow-type: tm+mt
source-wordcount: 1435
ht-degree: 84%

---

# Cópia de conteúdo para consistência do ambiente {#content-copy}

A Cópia de conteúdo no Cloud Manager permite que os usuários copiem conteúdo mutável sob demanda de ambientes de produção do Adobe Experience Manager 6.x hospedados no Adobe Managed Services para ambientes inferiores para fins de teste.

## Sobre cópia de conteúdo {#introduction}

Os dados atuais e reais são valiosos para fins de teste, validação e aceitação do usuário. A Cópia de conteúdo permite que você copie conteúdo do seu ambiente de produção AEM 6.x hospedado no AMS para ambientes de preparação ou desenvolvimento. Esse fluxo de trabalho permite realizar vários tipos de teste.

Um conjunto de conteúdo define o conteúdo a ser copiado. Um conjunto de conteúdo inclui uma lista de caminhos JCR com o conteúdo mutável a ser copiado. O conteúdo é movido de um ambiente de origem para um ambiente de destino. Essa operação é executada no mesmo programa Cloud Manager.

Os seguintes caminhos são permitidos em um conjunto de conteúdo:

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

Ao copiar o conteúdo, o ambiente de origem é a referência principal.

Quando você edita o conteúdo no ambiente de destino, o conteúdo de origem substitui-o, caso os caminhos correspondam.

Se os caminhos forem diferentes, o conteúdo da origem será mesclado com o conteúdo do destino.

### Permissões {#permissions}

Para usar o recurso Cópia de conteúdo, o usuário deve ser atribuído à função **Gerente de implantação** nos ambientes de origem e de destino.

## Criar um conjunto de conteúdo {#create-content-set}

Antes que qualquer conteúdo possa ser copiado, um conjunto de conteúdo deve ser definido. Depois de definidos, os conjuntos de conteúdo podem ser reutilizados para copiar o conteúdo.

**Para criar um conjunto de conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, em **Serviços**, clique em ![Ícone de caixa](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de conteúdo**.

1. Próximo ao canto superior direito da página, clique em **Adicionar conjunto de conteúdo**.

   ![Conjuntos de conteúdo](/help/assets/content-sets.png)

1. Na caixa de diálogo **`Add Content Set`**, na guia **Detalhes**, nos campos **Nome** e **Descrição**, digite um nome e uma descrição opcional para o conjunto de conteúdo e clique em **Continuar**.

   ![Detalhes do conjunto de conteúdo](/help/assets/add-content-set-details.png)

1. Na guia **Caminhos de conteúdo**, no campo de texto **Caminho**, especifique um caminho para o conteúdo que possa ser alterado e incluído no conjunto de conteúdo.

   Somente os caminhos que começam com `/content`, `/conf`, `/etc`, `/var/workflow/models` ou `/var/commerce` podem ser incluídos.

1. Clique no ![Ícone de adição de pasta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) **Adicionar caminho** para adicionar (ou incluir) o caminho no conjunto de conteúdo.

1. (Opcional) Se necessário, adicione caminhos adicionais (até 50) repetindo as duas etapas anteriores. Caso contrário, continue para a próxima etapa.

   ![Adicionar caminhos ao conjunto de conteúdo](/help/assets/add-content-set-paths.png)

1. (Opcional) Para refinar seu conjunto de conteúdo, você pode especificar subcaminhos dentro de um caminho de conteúdo incluído que deve ser excluído.

   1. À direita de um caminho de conteúdo incluído que você deseja excluir, clique em ![Ícone de exclusão de pasta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. No campo de texto, digite um caminho relativo ao caminho raiz visto na caixa de diálogo.
   1. Clique no ![Ícone de apagar pasta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **Excluir caminho**.
   1. Repita as etapas i, ii e iii para adicionar mais caminhos excluídos; não há limite. Caso contrário, continue para a próxima etapa.

   ![Excluir caminhos](/help/assets/add-content-set-paths-excluded.png)

1. (Opcional) Siga qualquer um destes procedimentos:

   1. Clique no ícone de ![X tamanho 500](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) à direita de um subcaminho excluído para apagá-lo.
   1. Clique no ícone de ![Mais](https://spectrum.adobe.com/static/icons/ui_18/More.svg) à direita de um caminho de conteúdo incluído e em **Editar** ou **Excluir**.

   ![Editar lista de caminhos](/help/assets/add-content-set-excluded-paths.png)

1. Clique em **Criar**. Agora você pode usar o conjunto de conteúdo para copiar conteúdo entre ambientes.

## Editar ou apagar um conjunto de conteúdo {#edit-content-set}

Para revelar os subcaminhos excluídos, expanda os caminhos configurados.

**Para editar ou apagar um conjunto de conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, em **Serviços**, clique em ![Ícone de caixa &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de conteúdo**.

1. Na tabela da página **Conjuntos de conteúdo**, clique no ícone de ![Mais](https://spectrum.adobe.com/static/icons/ui_18/More.svg) à direita de um caminho de conteúdo incluído e clique em **Editar** ou **Excluir**.

![Editar conjunto de conteúdo](/help/assets/edit-content-set.png)

## Copiar conteúdo {#copy-content}

Depois que um conjunto de conteúdo é criado, você pode usá-lo para copiar conteúdo.

Um ambiente pode estar indisponível para seleção se qualquer uma das seguintes condições se aplicar:

* O usuário não tem as permissões necessárias.
* No momento, um pipeline ou uma operação de cópia de conteúdo está em execução no ambiente.

**Para copiar conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, em **Serviços**, clique em ![Ícone de caixa &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de conteúdo**.

1. Na tabela da página **Conjuntos de conteúdo**, à direita de um caminho de conteúdo incluído que você deseja copiar, clique no ícone ![Mais](https://spectrum.adobe.com/static/icons/ui_18/More.svg) e em **Copiar conteúdo**.

   ![Cópia de conteúdo](/help/assets/copy-content.png)

1. Na caixa de diálogo **Copiar conteúdo**, selecione o ambiente de **Origem** e o ambiente de **Destino** para sua ação de cópia de conteúdo.

   * As regiões em um ambiente de destino devem ser um subconjunto das regiões em um ambiente de origem.
   * Os problemas de compatibilidade são verificados antes de executar uma ação de cópia de conteúdo. Ao selecionar o ambiente de **Destino**, o sistema valida automaticamente os ambientes de origem e destino. Se a validação falhar, o processo será interrompido e uma mensagem de erro será exibida na caixa de diálogo que explica o motivo da falha.

     ![Copiar conteúdo](/help/assets/copying-content.png)

1. (Opcional) Siga qualquer um destes procedimentos:

   1. Para *reter* os caminhos excluídos no ambiente de destino, marque **`Do not delete excluded paths from destination`**. Essa configuração mantém intactos os caminhos excluídos especificados no conjunto de conteúdo.
   1. Para *remover* os caminhos excluídos no ambiente de destino, desmarque **`Do not delete excluded paths from destination`**. Essa configuração apaga os caminhos excluídos especificados no conjunto de conteúdo.
   1. Para copiar o histórico de versões de caminhos do ambiente de origem para o ambiente de destino, marque **Copiar versões**. O processo de cópia de conteúdo é muito mais rápido quando o histórico da versão *não* é copiado.

1. Clique em **Copiar**. O status do processo de cópia é exibido no console do conjunto de conteúdo selecionado.

## Verificar o status de uma cópia de conteúdo {#copy-activity}

É possível monitorar o status dos processos de cópia na página **Atividade de cópia de conteúdo**.

**Para verificar o status de uma cópia de conteúdo:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. No canto superior esquerdo da página, clique em ![Mostrar ícone de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir o menu do lado esquerdo.

1. No menu do lado esquerdo, em **Serviços**, clique em ![ícone Histórico](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **Copiar Atividade de Conteúdo**.

   ![Atividade de cópia de conteúdo](/help/assets/copy-content-activity.png)

   Um processo de cópia de conteúdo pode ter um dos seguintes status:

   | Status | Descrição |
   | --- | --- |
   | Em andamento | O processo de cópia de conteúdo está em andamento. |
   | Concluído | O processo de cópia de conteúdo foi concluído com sucesso. |
   | Falhou | O processo de cópia de conteúdo falhou. |

## Limitações da cópia de conteúdo {#limitations}

* Não é possível executar a cópia de conteúdo de um ambiente inferior para um superior.
* Só é possível executar a cópia de conteúdo em níveis equivalentes. Especificamente, isso significa autor para autor ou publicação para publicação.
* Não é possível copiar conteúdo entre programas e entre regiões.
* A cópia de conteúdo para a topologia baseada no armazenamento de dados em nuvem só pode ser executada quando os ambientes de origem e de destino estão no mesmo provedor de nuvem e na mesma região.
* Não é possível executar operações de cópia de conteúdo simultâneas no mesmo ambiente.
* Não é possível executar a cópia de conteúdo se houver uma operação ativa em execução no ambiente de destino ou de origem, como um pipeline de CI/CD.
* A cópia de conteúdo não deve ser usada como uma ferramenta de clonagem ou espelhamento porque não pode rastrear conteúdos movidos ou excluídos na origem.
* Uma cópia de conteúdo não pode ser pausada ou cancelada depois de iniciada.
* A cópia de conteúdo duplica ativos e metadados do Dynamic Media do ambiente superior para o ambiente inferior selecionado. Os ativos copiados precisam ser reprocessados usando o [fluxo de trabalho dos ativos do processo DAM](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/assets/using/assets-workflow) no ambiente inferior. Esse reprocessamento é necessário para usar a respectiva configuração do Dynamic Media.
* [Não há suporte para configurações do Dynamic Media com tamanhos de ativos superiores a 2 GB habilitados](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb).
* As regiões do ambiente de destino devem ser iguais às regiões do ambiente de origem, ou um subconjunto delas.

## Problemas conhecidos da Cópia de conteúdo {#known-issues}

{{content-copy-known-issues}}
