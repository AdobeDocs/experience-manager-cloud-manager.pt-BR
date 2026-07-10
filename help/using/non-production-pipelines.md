---
title: Adicionar um pipeline de não produção
description: Saiba como usar o Cloud Manager para criar e configurar pipelines de não produção para implantar seu código.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
TQID: https://experienceleague.adobe.com/Dj7SjKdao6RU-cIS7D1AQxg5qpKrJMTcYQJBfiqc-Gg
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 4c73ab16ff7eab406c31a6d26cdd09360a94b3ea
workflow-type: tm+mt
source-wordcount: 2080
ht-degree: 22%

---

# Adicionar um pipeline de não produção {#configuring-non-production-pipelines}

Saiba como usar o Cloud Manager para criar e configurar pipelines de não produção para implantar seu código. Se desejar começar com uma visão geral mais conceitual de como funcionam os pipelines no Cloud Manager, consulte [Pipelines de CI/CD.](/help/overview/ci-cd-pipelines.md)

## Visão geral {#overview}

Ao usar o bloco **Pipelines** no [!UICONTROL Cloud Manager], o **Gerenciador de implantação** pode criar dois tipos diferentes de pipelines.

* **Pipelines de produção** - Um pipeline de produção é composto por uma série de etapas orquestradas que têm o objetivo de levar o código-fonte até a produção.
* **Pipelines de não produção** - um pipeline não relacionado à produção serve principalmente para executar verificações de qualidade de código ou implantar o código-fonte em um ambiente de desenvolvimento.

Este documento se concentra em pipelines de não produção. Para mais detalhes sobre como configurar pipelines de produção, consulte o documento [Configuração de pipelines de produção](/help/using/production-pipelines.md).

Existem dois tipos de pipelines de não produção:

* **Pipelines de qualidade do código**: executam verificações de qualidade de código em uma ramificação do Git e executam as etapas de qualidade de código e de criação.
* **Pipelines de implantação**: além de executar as etapas de qualidade de código de criação como os pipelines de qualidade do código, esses pipelines implantam o código em um ambiente de não produção.

>[!NOTE]
>
>Você não pode configurar um pipeline até que seu repositório Git associado tenha pelo menos uma ramificação e a [configuração do programa](/help/getting-started/program-setup.md) seja concluída. Consulte os  [Repositórios do Cloud Manager](/help/managing-code/managing-repositories.md) para saber como adicionar e gerenciar repositórios no Cloud Manager.

## Adicionar um pipeline de não produção {#add-non-production-pipeline}

Depois de configurar um programa e pelo menos um ambiente na interface do usuário do Cloud Manager, você pode adicionar pipelines de não produção. Use esses pipelines para testar a qualidade do código antes de implantar em ambientes de produção.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selecione a organização e o programa apropriados.

1. Na tela inicial do Cloud Manager, abra o cartão Pipelines e clique em **Adicionar** e selecione **Adicionar pipeline de não produção**.

   ![Adicionar pipeline de não produção](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Na guia **Configuração** da caixa de diálogo **Adicionar pipeline de não produção**, selecione o tipo de pipeline que deseja criar, uma das seguintes opções:

   * **Pipeline de Qualidade do Código** - Cria um pipeline que compila o código, executa testes de unidade e avalia a qualidade do código sem implantar em um ambiente.
   * **Pipeline de Implantação** - Cria um pipeline que compila o código, executa testes de unidade, avalia a qualidade do código e realiza a implantação em um ambiente.

   ![Escolha o tipo de pipeline](/help/using/assets/add-non-production-pipeline-cm-ams.png)

>[!BEGINTABS]

>[!TAB Pipeline de qualidade de código - guia Configuração]

| Seção | Opção | Descrição |
| --- | --- | --- |
| **Configuração de pipeline** | **Nome do pipeline de não produção** | Insira uma descrição para o pipeline no campo **Nome do pipeline de não produção**. |
|  | **Testando** | Visível somente ao editar um pipeline de não produção.<br>A interface do usuário mostra as categorias de teste que o pipeline executa como parte da validação de qualidade do código.<ul><li>**Teste de Código Estático** - Analisa o código quanto a problemas de qualidade e correção.<li>**Teste de carga/desempenho** - Avalia o comportamento relacionado ao desempenho como parte do teste de pipeline.<li>**Teste de segurança** - Verifica o código e a saída do pipeline em busca de problemas relacionados à segurança. |
| **Opções de implantação** | **Acionador da implantação** | <ul><li>**Manual**: permite iniciar manualmente o pipeline.<li>**Sobre alterações do Git**: inicia o pipeline sempre que confirmações forem adicionadas à ramificação Git configurada. Com essa opção, ainda é possível iniciar o pipeline manualmente, conforme necessário. |
|  | **Comportamento de Falhas de Métricas Importantes** | <ul><li>**Perguntar sempre**: esse comportamento é a configuração padrão e exige intervenção manual em qualquer falha importante.<li>**Falha imediata** - Se selecionado, o pipeline será cancelado sempre que ocorrer uma falha importante. É basicamente semelhante a um usuário que rejeita manualmente cada falha.<li>**Continuar imediatamente** - Se selecionado, o pipeline continuará automaticamente sempre que ocorrer uma falha importante. É basicamente semelhante a um usuário que aprova manualmente cada falha.</li></ul> |
|  | **Aprovar após a caixa de seleção Implantação de Preparo** | Visível somente ao editar um pipeline de não produção.<br>Selecione esta opção para exigir aprovação após a implantação no ambiente de preparo antes que o pipeline possa continuar. Se essa opção não estiver selecionada, o pipeline continuará com base no comportamento configurado. |

>[!TAB Pipeline de Implantação - Guia Configuração]

| Seção | Opção | Descrição |
| --- | --- | --- |
| **Configuração de pipeline** | **Nome do pipeline de não produção** | Insira uma descrição para o pipeline no campo **Nome do pipeline de não produção**. |
|   | **Ambiente de Implantação Qualificado** | Se o pipeline for um pipeline de implantação, você deverá selecionar quais ambientes o Cloud Manager implanta o código. |
|   | **Testando** | Visível somente ao editar um pipeline de não produção.<br>A interface do usuário mostra as categorias de teste que o pipeline executa como parte da validação de qualidade do código.<ul><li>**Teste de Código Estático** - Analisa o código quanto a problemas de qualidade e correção.<li>**Teste de carga/desempenho** - Avalia o comportamento relacionado ao desempenho como parte do teste de pipeline.<li>**Teste de segurança** - Verifica o código e a saída do pipeline em busca de problemas relacionados à segurança.</li></ul> |
| **Opções de implantação** | **Acionador da implantação** | <ul><li>**Manual**: permite iniciar manualmente o pipeline.<li>**Sobre alterações do Git**: inicia o pipeline sempre que confirmações forem adicionadas à ramificação Git configurada. Com essa opção, ainda é possível iniciar o pipeline manualmente, conforme necessário. |
|   | **Comportamento de Falhas de Métricas Importantes** | <ul><li>**Perguntar sempre** - A configuração padrão e solicita que o usuário decida como proceder quando uma métrica importante falhar.<li>**Falha imediata** - O pipeline é cancelado sempre que uma métrica importante falha. É como emular um usuário que rejeita manualmente cada falha.<li>**Continuar imediatamente** - O pipeline continua automaticamente sempre que uma métrica importante falha. É como emular um usuário que aprova manualmente cada falha.</li></ul> |
|  | **Aprovar após a caixa de seleção Implantação de Preparo** | Visível somente ao editar um pipeline de não produção.<br>Selecione esta opção para exigir aprovação após a implantação no ambiente de preparo antes que o pipeline possa continuar. Se essa opção não estiver selecionada, o pipeline continuará com base no comportamento configurado. |
|  | **Ignorar alterações no Balanceador de Carga** | Selecione esta opção para impedir que o pipeline faça alterações no balanceador de carga durante a implantação. |
|  | **Configuração do Dispatcher** | O **Gerenciador de Implantação** pode configurar um conjunto de caminhos de conteúdo que são invalidados ou removidos do cache do AEM Dispatcher quando um pipeline é executado. O Cloud Manager executa essas ações de cache como parte da etapa do pipeline de implantação, logo após a implantação de qualquer pacote de conteúdo. Essas configurações usam o comportamento padrão do Dispatcher do AEM. Para configurar o `Dispatcher`, faça o seguinte:<ul><li>Em **PATH**, forneça um caminho de conteúdo que você deseja que o pipeline limpe ou invalide.<li>Em **TIPO**, selecione a ação a ser tomada nesse caminho.<ul><li>**Liberar** - Executa uma exclusão de cache no caminho especificado.</li><li>**Invalidar** - Executa uma invalidação de cache, semelhante a quando o conteúdo é ativado de uma instância de criação para uma instância de publicação.</li><li>Clique em **Adicionar caminho** para adicionar o caminho especificado. É possível adicionar até 100 caminhos por ambiente.</li></ul> |
| **Pipeline** | Caixa de seleção **Auditoria de experiência** | Selecione essa opção para incluir uma etapa da Auditoria de experiência no pipeline. Quando ativado, o pipeline inclui a etapa Auditoria de experiência após a guia Código Source. |

>[!ENDTABS]

1. No canto inferior direito da caixa de diálogo **Adicionar pipeline de não produção**, clique em **Continuar**.
1. Selecione o tipo de código que o pipeline está configurado para criar e implantar.

>[!BEGINTABS]

>[!TAB Guia Código Source - Código de pilha completa]

Implanta o aplicativo AEM completo, incluindo o código do aplicativo e, por padrão, a configuração no nível da Web.

>[!NOTE]
>
>Se um pipeline de código de pilha completa já existir para o ambiente selecionado, essa seleção ficará desativada.

| Seção | Opção | Descrição |
| --- | --- | --- |
| **código Source** | **Repositório** | Na lista suspensa, escolha o repositório Git que o pipeline usa como origem. O Cloud Manager cria código a partir do repositório escolhido aqui. |
|   | **Ramificação Git** | Na lista suspensa, escolha em qual ramificação o pipeline deve ser criado no repositório selecionado. O padrão é `main`. O pipeline usa a ramificação escolhida como origem para a compilação e a implantação. Se necessário, clique em **Atualizar** para atualizar a lista de ramificações disponíveis para o repositório selecionado. Use esta opção se uma ramificação criada recentemente não aparecer na lista. |
|   | **Estratégia de compilação** | <ul><li>**Compilação Completa** - Cria todos os módulos no repositório sempre<li>**Compilação Inteligente** - Compila apenas módulos que foram alterados desde a última confirmação.<br>Saiba mais sobre [como usar o Smart Build em um pipeline de não produção](#about-smart-build).</li></ol> |
|   | **Ignorar a caixa de seleção Configuração da Camada da Web** | Selecione esta opção para ignorar a implantação da configuração no nível da Web em um pipeline de código de Empilhamento completo. Deixe a opção desmarcada para implantar a configuração no nível da Web junto com o código do pipeline. |
| **Pipeline** | Caixa de seleção **Auditoria de experiência** | Selecione essa opção para incluir uma etapa da Auditoria de experiência no pipeline. Quando ativado, o pipeline inclui a etapa Auditoria de experiência após a guia Código Source. |

>[!TAB Código Source - Configuração da Camada da Web]

Implanta apenas a configuração no nível da Web, como propriedades do Dispatcher usadas para armazenar, processar e entregar páginas da Web ao cliente. Ao selecionar **Configuração da camada da Web**, o Cloud Manager cria um pipeline dedicado à implantação da configuração da camada da Web.

Se um pipeline de pilha completa já existir, o Cloud Manager exibe um aviso de que a criação de um pipeline de configuração no nível da Web faz com que o pipeline de pilha completa existente ignore a configuração no nível da Web. Depois de criar o pipeline de configuração no nível da Web, o Cloud Manager gerencia as implantações de configuração no nível da Web por meio desse pipeline, em vez do pipeline de pilha completa.

>[!NOTE]
>
>Se um pipeline de configuração no nível da Web já existir para o ambiente selecionado, essa seleção será desativada. Em um dado momento, somente pode haver um pipeline de configuração no nível da Web por ambiente.

| Seção | Opção | Descrição |
| --- | --- | --- |
| **código Source** | **Repositório** | Na lista suspensa, selecione o repositório Git que contém a configuração no nível da Web. |
|   | **Ramificação Git** | Selecione a ramificação no repositório escolhido que o Cloud Manager usa para a implantação. Se necessário, clique em **Atualizar** para atualizar a lista de ramificações disponíveis para o repositório selecionado. Use esta opção se uma ramificação criada recentemente não aparecer na lista. |
|   | **Localização do código** | Insira o caminho no repositório selecionado que contém a configuração da camada da Web a ser implantada. O local padrão é a raiz do repositório (`/`). |

>[!NOTE]
>
>Se a Localização do código não apontar para a localização do código do Dispatcher, o código de aplicativo adicional pode ser extraído para o pacote de artefatos e implantado no Dispatcher, fazendo com que o Apache falhe na reinicialização e o pipeline falhe. Defina o caminho correto para os arquivos do dispatcher no repositório.

>[!ENDTABS]

1. Clique em **Salvar**.

## Sobre o uso do Smart Build no pipeline de não produção{#about-smart-build}

A **Compilação Inteligente** do Cloud Manager é uma estratégia de compilação otimizada para pipelines de não produção. O Smart Build reduz os tempos de criação ao armazenar em cache módulos e recriar apenas os módulos que foram alterados desde a última execução bem-sucedida. Os módulos inalterados são reutilizados do cache, enquanto apenas os módulos modificados e suas dependências são recriados, melhorando a eficiência dos workflows de desenvolvimento iterativos.

O Smart Build está disponível atualmente para o seguinte:

* Pipelines de qualidade do código.
* Pipelines de implantação de pilha completa de desenvolvimento, preparo e não produção.


>[!NOTE]
>
>A primeira execução após a ativação da Compilação inteligente se comporta como uma Compilação completa porque o cache está vazio.

O Smart Build é recomendado quando você tem o seguinte:

* Você está desenvolvendo e confirmando ativamente alterações incrementais frequentes.
* Seu projeto contém vários módulos Maven.
* As compilações completas estão demorando muito.

O Smart Build nem sempre é ideal quando você tem o seguinte:

* Sua build depende muito de plug-ins que executam operações fora do gráfico de dependência do Maven.
* Você precisa da validação completa de reconstrução em cada execução.

### Entender o desempenho da build{#smart-build-performance}

O ganho de desempenho com o uso do Smart Build depende de vários fatores, incluindo os seguintes:

* O número de módulos no projeto.
* A frequência e o escopo das alterações de código.
* A distribuição de dependências entre módulos.

Geralmente, projetos com muitos módulos independentes podem ver a maior melhoria.

### Recusa de cache por módulo{#smart-build-cache-optout}

O Smart Build fornece controle refinado que permite desativar o armazenamento em cache de módulos específicos. Essa capacidade é útil quando determinados módulos:

* Use plug-ins, como `exec-maven-plugin` ou `maven-antrun-plugin`.
* Executar operações de arquivo não rastreadas pelas dependências do Maven.
* Produza resultados inconsistentes quando armazenados em cache.

### Desativar armazenamento em cache para um módulo{#smart-build-disable-caching}

Você pode adicionar a seguinte propriedade ao `pom.xml` do módulo afetado:

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

Essa sintaxe força o módulo a ser recriado em cada execução de pipeline, enquanto outros módulos continuam a se beneficiar do armazenamento em cache.

### Limitações e considerações ao usar o Smart Build{#smart-build-limitations}

Lembre-se do seguinte ao usar o Smart Build:

* O Smart Build depende da análise de dependência do Maven.
* As alterações fora do gráfico de dependência não podem acionar recriações.
* Alguns plug-ins podem não ser totalmente compatíveis com o armazenamento em cache.
* Você pode voltar para a **Compilação completa** a qualquer momento editando o pipeline de não produção.

Se você encontrar um comportamento de compilação inesperado, considere desabilitar o cache de módulos específicos ou alternar temporariamente sua estratégia de compilação para **Compilação Completa**.

### Solução de problemas do Smart Build{#smart-build-troubleshoot}

| Problema | Soluções sugeridas |
| --- | --- |
| Os resultados da build são inconsistentes | · Desabilitar o cache para os módulos afetados.<br>· Verificar o comportamento do plug-in (especialmente `exec`/`antrun` plug-ins). |
| Sem melhoria de desempenho | · Verifique se várias execuções ocorreram (aquecimento de cache).<br>· Verifique se a maioria dos módulos está mudando com frequência. |
| Artefatos inesperados ou alterações ausentes | · Revise se se as alterações estão fora do rastreamento de dependência Maven.<br>· Use **Compilação completa** para verificação. |

Consulte [Adicionar um pipeline de não produção](#add-non-production-pipeline) para habilitar o Smart Build.



<!-- 
1. If you chose to add a **Deployment Pipeline**, select the target deployment environment from the **Eligible Deployment Environments** dropdown.

1. Enter the repository where the pipeline should retrieve the code.

   * **Repository** - Select the Git repository that the pipeline retrieves code from.
   * **Git Branch** - Select the branch in the Git repository that the selected pipeline retrieves code from.

1. Define your deployment options.

   1. Under **Deployment Trigger**, define what event activates the pipeline.

      * **Manual** - Lets you manually start the pipeline.
      * **On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required.

   1. For deployment pipelines, under **Important Metric Failures Behavior**, define the behavior of the pipeline when an important failure is encountered in any of the quality gates.

       * **Ask every time** - The default setting and requires manual intervention on any important failure.
       * **Fail Immediately** - Cloud Manager cancels the pipeline whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
       * **Continue Immediately** - The pipeline proceeds automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

   1. **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths that Cloud Manager invalidates or flushes from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:

      1. Under **PATH** provide a content path.
      1. Under **TYPE**, select the action to be taken on that path.

         * **Flush** - Perform a cache deletion.
         * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
         
      1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

1. Click **Save**.
-->

## Próximas etapas {#the-next-steps}

Depois de configurar o pipeline, você pode implantar seu código. Consulte [Implantação de código](/help/using/code-deployment.md) para obter mais detalhes.

## Tutorial em vídeo {#video-tutorial}

Este vídeo fornece uma visão geral do processo de criação de pipeline, que é detalhado neste documento.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
