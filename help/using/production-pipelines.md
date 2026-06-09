---
title: Adicionar um pipeline de produção
description: Saiba como usar o Cloud Manager para criar e configurar pipelines de produção para implantar seu código.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
TQID: https://experienceleague.adobe.com/WH6W8bZNCWo0BAGLwnMOPpB3bk5P6Fd7c5b-dRT5Vc0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: badb64b816e83ca08a39b2b39eda13335f6a3c1d
workflow-type: tm+mt
source-wordcount: 1665
ht-degree: 73%

---

# Adicionar um pipeline de produção {#configuring-production-pipelines}

Saiba como usar o Cloud Manager para criar e configurar pipelines de produção para implantar seu código. Se desejar começar com uma visão geral mais conceitual de como funcionam os pipelines no Cloud Manager, consulte [Pipelines de CI/CD.](/help/overview/ci-cd-pipelines.md)

## Visão geral {#overview}

Você pode criar dois tipos diferentes de pipelines usando o bloco **Configurações de pipeline** no [!UICONTROL Cloud Manager].

* **Pipelines de produção**: um pipeline de produção é um pipeline com propósito específico composto por uma série de etapas orquestradas para levar o código fonte do seu repositório Git até a produção.
* **Pipelines de não produção** - Um pipeline de não produção é utilizado principalmente para executar verificações de qualidade de código ou implantar o código-fonte em um ambiente de desenvolvimento.

Este documento é voltado para pipelines de produção. Para obter detalhes sobre como configurar pipelines de não produção, consulte o documento [Configuração de pipelines de não produção.](/help/using/non-production-pipelines.md)

O **Gerenciador de implantação** é responsável pela configuração do pipeline. A configuração do pipeline consiste em:

1. Definição do acionador que iniciará o pipeline.
1. Definir os parâmetros que controlam a implantação de produção.
1. Configurar os parâmetros de teste de desempenho.

>[!NOTE]
>
>Um pipeline não pode ser configurado até que seu repositório Git associado tenha pelo menos uma ramificação e a [configuração do programa](/help/getting-started/program-setup.md) seja concluída.

## Adicionar um novo pipeline de produção {#adding-production-pipeline}

Após usar a interface do [!UICONTROL Cloud Manager] para configurar seu programa e definir pelo menos um ambiente, você poderá adicionar um pipeline de produção.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o cartão **Pipelines** na página **Visão geral do programa**.

1. Clique em **+Adicionar** e selecione **Adicionar pipeline de produção**.

   ![Adicionar um pipeline de produção](/help/assets/configure-pipelines/add-prod7.png)

1. A caixa de diálogo **Adicionar pipeline de produção** é aberta na guia **Configuração**, onde várias opções do pipeline devem ser definidas. Essas opções são agrupadas em seções que podem ser recolhidas e são descritas nas etapas a seguir.

   1. Forneça um nome descritivo para o pipeline no campo **Nome do pipeline**.

   1. Na seção **Ambientes**, você define o que aciona uma implantação e como ela deve ser realizada em cada ambiente.

      1. Na seção **PREPARO**, é possível definir como o pipeline é implantado em seu ambiente de preparo.

         * **Acionador de implantação** - Você tem as seguintes opções para definir os acionadores de implantação que iniciam o pipeline.

            * **Manual**: inicie o pipeline manualmente usando a interface do Cloud Manager.
            * **Sobre alterações do Git**: inicia o pipeline de CI/CD sempre que confirmações forem adicionadas à ramificação Git configurada. Com essa opção, ainda é possível iniciar o pipeline manualmente, conforme necessário.

         * **Comportamento de falhas de métricas importantes** - Durante a configuração ou edição do pipeline, o Gerenciador de implantação tem a opção de definir o comportamento do pipeline quando uma falha importante é encontrada em qualquer uma das portas de qualidade. As opções disponíveis são:

            * **Sempre perguntar**: a configuração padrão e requer intervenção manual em qualquer falha importante.
            * **Falhar imediatamente**: o pipeline será cancelado sempre que ocorrer uma falha importante. Emula um usuário que rejeita manualmente cada falha.
            * **Continuar imediatamente**: o pipeline continuará automaticamente sempre que ocorrer uma falha importante. Emula um usuário aprovando manualmente cada falha.

         ![Acionador de implantação](/help/assets/configure-pipelines/add-prod3.png)

         * **Opções de implantação** - Você pode acelerar determinadas tarefas de implantação.

            * **Aprovar após a implantação de preparo** - Essa aprovação ocorre após a implantação no ambiente de preparo, antes da realização de qualquer teste. Caso contrário, a aprovação ocorre antes da implantação da produção, que é feita após a conclusão de todos os testes.

            * **Ignorar alterações do balanceador de carga** - Não são efetuadas alterações no balanceador de carga.

         ![Opções de implantação de preparo](/help/assets/configure-pipelines/add-prod4.png)

         * **Configuração do Dispatcher**: a função **Gerenciador de implantação** pode configurar um conjunto de caminhos de conteúdo que serão invalidados ou liberados do cache do Dispatcher do AEM quando um pipeline for executado. Essas ações de cache são realizadas como parte da etapa do pipeline de implantação, logo após a implantação de qualquer pacote de conteúdo. Essas configurações usam o comportamento padrão do Dispatcher do AEM. Para configurar, faça o seguinte:

            1. Em **CAMINHO**, forneça um caminho de conteúdo.
            1. Em **TIPO**, selecione a ação a ser tomada nesse caminho.

               * **Limpeza** - Executa uma exclusão do cache.
               * **Invalidar** - Executa uma invalidação de cache, semelhante a quando o conteúdo é ativado de uma instância de criação para uma instância de publicação.

            1. Clique em **Adicionar caminho** para adicionar o caminho especificado. É possível adicionar até 100 caminhos por ambiente.

         ![Configuração do Dispatcher](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >Em geral, o uso da ação de invalidação é preferível, mas pode haver casos em que a limpeza será necessária, especialmente ao usar bibliotecas de clientes em HTML do AEM.

      1. Na seção **PRODUÇÃO**, é possível definir como o pipeline é implantado em seu ambiente de produção.

         * **Opções de implantação** - Você pode definir os parâmetros que controlam a implantação de produção.

            * **Usar aprovação de ativação**: alguém com a função de **Proprietário da empresa**, **Gerenciador de projetos** ou **Gerenciador de Implantação** por meio da interface do [!UICONTROL Cloud Manager] deve aprovar manualmente uma implantação.
            * **Agendado**: interrompe o pipeline antes da implantação de produção para permitir o seu agendamento. Se essa opção estiver selecionada, o pipeline será interrompido após a implantação no ambiente de preparo e solicitará que o usuário execute a ação.
               * **`Now`**: realiza a implantação na produção imediatamente, concluindo efetivamente o pipeline.
               * **Data**: permite o agendamento do horário em que a implantação deverá ser concluída.
               * **Parar execução**: interrompe a implantação para a produção.

           >[!TIP]
           >
           >Consulte [Implantação do código](/help/using/code-deployment.md) para saber como programar a implantação ou executar o pipeline imediatamente.

            * **Usar a supervisão do CSE**: se essa opção for selecionada, será solicitado o auxílio de um CSE (Engenheiro de sucesso do cliente) para iniciar a implantação. Ao criar ou editar um pipeline quando essa opção estiver habilitada, a função **Gerente de implantação** terá as seguintes opções.

               * **Qualquer CSE**: permite que qualquer CSE disponível inicie a implantação.
               * **Meu CSE**: permite que somente o CSE específico atribuído ao cliente inicie a implantação. Essa opção também se aplica ao backup do CSE designado se o CSE atribuído não estiver disponível.

           ![Opções de implantação de produção](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configuração do Dispatcher**: define a configuração do Dispatcher para o ambiente de produção. As opções são as mesmas do ambiente de preparo.

1. Clique em **Continuar** para avançar para a guia **Código Source**, na qual você seleciona o tipo de código para implantar e configurar o repositório de origem.

   1. Em **Selecionar código para implantar**, escolha o tipo de implantação:

      * **[Código de pilha completa](#full-stack-code)** - Código para o aplicativo AEM completo.
      * **[Configuração da Camada da Web](#web-tier-config)** - Propriedades do Dispatcher para armazenar, processar e entregar páginas da Web ao cliente.

      Consulte [Pipelines de CI/CD](/help/overview/ci-cd-pipelines.md#code-sources) para obter mais informações sobre esses tipos de implantação. As etapas restantes para concluir a configuração do pipeline dependem do tipo selecionado. Siga os links acima para ir até a seção relevante deste documento.

1. Clique em **Continuar** para avançar até a guia **Teste de preparo**, onde é possível configurar o teste de desempenho do AEM Sites e do AEM Assets, dependendo das licenças de produto que você possui. {#stage-testing}

   >[!TIP]
   >
   >Consulte [Teste de qualidade do código](/help/using/code-quality-testing.md#performance-testing) para obter mais detalhes sobre as opções disponíveis na guia **Teste de preparo**.

   1. Na seção **Entrega de conteúdo de sites/Peso de carga distribuído**, configure o teste de desempenho do site com base na ponderação de solicitações de página entre três conjuntos de páginas. Você pode habilitar ou desabilitar os conjuntos de páginas conforme necessário.

      * **Páginas populares ativas**
      * **Outras páginas ativas**
      * **Novas páginas**

      ![Peso de carregamento dos sites](/help/assets/configure-pipelines/add-prod8.png)

   1. Na seção **Distribuição de teste de desempenho de ativos**, você define a distribuição de teste de imagens e PDFs, bem como de seus próprios ativos de teste.

      * **Imagens** - Use o controle deslizante para ajustar a divisão do teste entre imagens e PDFs.
      * **PDF** - Use o controle deslizante para ajustar a divisão do teste entre imagens e PDFs.

      * Defina seus próprios ativos personalizados fazendo upload deles.

         1. **FORMATO** - Escolha se o ativo personalizado é um PDF de uma imagem.
         1. **NOME DE ARQUIVO** - Use o botão do navegador de arquivos para selecionar uma imagem de sua máquina local.
         1. **Adicionar arquivo de teste** - Clique para fazer upload do ativo selecionado.

      ![Distribuição de testes de ativos](/help/assets/configure-pipelines/add-prod6.png)

1. Clique em **Salvar** para concluir a adição do pipeline de produção.

### Código de pilha completa {#full-stack-code}

Um pipeline de código de pilha completa implanta compilações de código de back-end e front-end juntamente com a configuração HTTPD/Dispatcher.

>[!NOTE]
>
>Se um pipeline de produção de pilha completa já existir, essa seleção será desativada.

**Para configurar um pipeline de produção com código de pilha completa:**

1. Na guia **Código Source**, defina as seguintes opções.

   * **Repositório**: define de qual repositório Git o pipeline deve recuperar o código.

   >[!TIP]
   >
   >Consulte o documento [Configuração do programa](/help/getting-started/program-setup.md) para saber como adicionar e gerenciar repositórios no Cloud Manager.

   * **Ramificação Git** - Define de qual ramificação o pipeline deve recuperar o código.
   * **Ignorar configuração no nível da Web**: quando essa opção está marcada, o pipeline não implanta sua configuração no nível da Web. Se um pipeline de configuração no nível da Web já existir para o mesmo ambiente, essa caixa de seleção será selecionada e desabilitada automaticamente, pois a configuração no nível da Web é gerenciada por esse pipeline. Quando não existir um pipeline de configuração no nível da Web, você pode selecionar ou desmarcar essa opção para controlar se o pipeline de pilha completa implanta a configuração do Dispatcher.

   ![Origem do código de pilha completa](/help/assets/configure-pipelines/add-prod-fullstack-source.png)

1. Clique em **Continuar** para avançar para a guia **Teste de Preparo**. Consulte [Teste de preparo](#stage-testing) para obter detalhes.

### Configuração da camada da Web {#web-tier-config}

Um pipeline de configuração no nível da Web implanta somente a configuração HTTPD/Dispatcher. Consulte [Pipelines de CI/CD](/help/overview/ci-cd-pipelines.md#deployment-types) para obter mais detalhes sobre esse tipo de pipeline.

>[!NOTE]
>
>Se um pipeline de produção de configuração no nível da Web já existir, essa seleção será desabilitada.

Se você criar um pipeline de configuração no nível da Web para um ambiente com um pipeline de pilha completa existente, a configuração no pipeline de pilha completa será ignorada. Essa alteração afeta somente a configuração no nível da Web nesse ambiente.

**Para configurar um pipeline de produção de configuração no nível da Web:**

1. Na guia **Código Source**, defina as seguintes opções.

   * **Repositório** - Na lista suspensa, selecione o repositório Git que contém a configuração da camada da Web.
   * **Ramificação Git** - Selecione a ramificação no repositório escolhido que a Cloud Manager usa para a implantação.
   * **Localização do Código** - Insira o caminho no repositório selecionado que contém a configuração da camada da Web a ser implantada. O local padrão é a raiz do repositório (`/`).

   >[!NOTE]
   >
   >Se a Localização do código não apontar para a localização do código do Dispatcher, o código de aplicativo adicional pode ser extraído para o pacote de artefatos e implantado no Dispatcher, fazendo com que o Apache falhe na reinicialização e o pipeline falhe. Defina o caminho correto para os arquivos do dispatcher no repositório.

   ![Fonte de configuração da camada da Web](/help/assets/configure-pipelines/add-prod-webtier-source.png)

1. Clique em **Continuar** para avançar para a guia **Teste de Preparo**. Consulte [Teste de preparo](#stage-testing) para obter detalhes.

## Próximas etapas {#the-next-steps}

Depois de configurar o pipeline, você implantará o código. Consulte [Implantação de código](/help/using/code-deployment.md) para obter mais detalhes.

## Tutorial em vídeo {#video-tutorial-one}

Este vídeo fornece uma visão geral do processo de criação de pipeline, que é detalhado neste documento.

>[!VIDEO](https://video.tv.adobe.com/v/327605?captions=por_br)
