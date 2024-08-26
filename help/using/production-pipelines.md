---
title: Configurar pipelines de produção
description: Saiba como usar o Cloud Manager para criar e configurar pipelines de produção para implantar seu código.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1247'
ht-degree: 57%

---


# Configurar pipelines de produção {#configuring-production-pipelines}

Saiba como usar o Cloud Manager para criar e configurar pipelines de produção para implantar seu código. Se desejar começar com uma visão geral mais conceitual de como funcionam os pipelines no Cloud Manager, consulte [Pipelines de CI/CD.](/help/overview/ci-cd-pipelines.md)

## Visão geral {#overview}

Você pode criar dois tipos diferentes de pipelines usando o bloco **Configurações de pipeline** no [!UICONTROL Cloud Manager].

* **Pipelines de produção** - Um pipeline de produção é composto por uma série de etapas orquestradas que têm o objetivo de levar o código-fonte do seu repositório Git até a produção.
* **Pipelines de não produção** - Um pipeline de não produção é utilizado principalmente para executar verificações de qualidade de código ou implantar o código-fonte em um ambiente de desenvolvimento.

Este documento é voltado para pipelines de produção. Para obter detalhes sobre como configurar pipelines de não produção, consulte o documento [Configuração de pipelines de não produção.](/help/using/non-production-pipelines.md)

O **Gerenciador de implantação** é responsável pela configuração do pipeline. A configuração do pipeline consiste em:

1. Definir o acionador que inicia o pipeline.
1. Definir os parâmetros que controlam a implantação de produção.
1. Configurar os parâmetros de teste de desempenho.

>[!NOTE]
>
>Um pipeline não pode ser configurado até que seu repositório Git associado tenha pelo menos uma ramificação e a [configuração do programa](/help/getting-started/program-setup.md) seja concluída.

## Adicionar um novo pipeline de produção {#adding-production-pipeline}

Depois de usar a interface do usuário do [!UICONTROL Cloud Manager] para configurar seu programa e definir pelo menos um ambiente, você estará pronto para adicionar um pipeline de produção.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o cartão **Pipelines** na página **Visão geral do programa**.

1. Clique em **+Adicionar** e selecione **Adicionar pipeline de produção**.

   ![Adicionar um pipeline de produção](/help/assets/configure-pipelines/add-prod1.png)

1. A caixa de diálogo **Adicionar pipeline de produção** é aberta na guia **Configuração**, onde várias opções do pipeline devem ser definidas. Essas opções são agrupadas em seções que podem ser recolhidas e são descritas nas etapas a seguir.

   1. Forneça um nome descritivo para o pipeline no campo **Nome do pipeline**.

   1. Na seção **Código Source**, você define de onde o pipeline recupera o código que ele processa.

      * **Repositório** - Define qual repositório Git o pipeline deve recuperar o código.

      >[!TIP]
      >
      >Consulte o documento [Configuração do programa](/help/getting-started/program-setup.md) para saber como adicionar e gerenciar repositórios no Cloud Manager.

      * **Ramificação Git** - Define de qual ramificação o pipeline selecionado deve recuperar o código.
      * **Localização do código** - Define o caminho na ramificação do repositório selecionado a partir do qual o pipeline deve recuperar o código.

      ![Definir repositórios para o pipeline](/help/assets/configure-pipelines/add-prod2.png)

   1. Na seção **Ambientes**, você define o que aciona uma implantação e como ela deve ser realizada em cada ambiente.

      1. Na seção **PREPARO**, é possível definir como o pipeline é implantado em seu ambiente de preparo.

         * **Acionador de implantação** - Você tem as seguintes opções para definir os acionadores de implantação que iniciam o pipeline.

            * **Manual** - Inicie o pipeline manualmente usando a interface do usuário do Cloud Manager.
            * **Sobre Alterações do Git** - Inicie o pipeline de CI/CD sempre que confirmações forem adicionadas à ramificação Git configurada. Com essa opção, ainda é possível iniciar o pipeline manualmente, conforme necessário.

         * **Comportamento de falhas de métricas importantes** - Durante a configuração ou edição do pipeline, o Gerenciador de implantação tem a opção de definir o comportamento do pipeline quando uma falha importante é encontrada em qualquer uma das portas de qualidade. As opções disponíveis são:

            * **Pergunte sempre** - A configuração padrão e requer intervenção manual em todas as falhas importantes.
            * **Falha imediata** - O pipeline é cancelado sempre que ocorre uma falha importante. Ele emula um usuário que rejeita manualmente cada falha.
            * **Continuar imediatamente** - O pipeline continua automaticamente sempre que ocorre uma falha importante. Ele emula um usuário que aprova manualmente cada falha.

         ![Acionador de implantação](/help/assets/configure-pipelines/add-prod3.png)

         * **Opções de implantação** - Você pode acelerar determinadas tarefas de implantação.

            * **Aprovar após a implantação de preparo** - Essa aprovação ocorre após a implantação no ambiente de preparo, antes da realização de qualquer teste. Caso contrário, a aprovação ocorre antes da implantação de produção, que é feita após a conclusão de todos os testes.

            * **Ignorar alterações do balanceador de carga** - Não são efetuadas alterações no balanceador de carga.

         ![Opções de implantação de preparo](/help/assets/configure-pipelines/add-prod4.png)

         * **Configuração do Dispatcher** - O **Gerenciador de Implantação** pode configurar um conjunto de caminhos de conteúdo que são invalidados ou removidos do cache do AEM Dispatcher quando um pipeline é executado. Essas ações de cache são executadas como parte da etapa do pipeline de implantação, logo após a implantação de qualquer pacote de conteúdo. Essas configurações usam o comportamento padrão do Dispatcher do AEM. Para configurar, faça o seguinte:

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

            * **Usar aprovação GoLive** - Um usuário com a função de **Proprietário da Empresa**, **Gerente de Projetos** ou **Gerente de Implantação** por meio da interface do usuário do [!UICONTROL Cloud Manager] deve aprovar manualmente uma implantação.
            * **Agendado** - Interrompe o pipeline antes da implantação de produção para permitir que ele seja agendado. Se essa opção estiver selecionada, o pipeline será interrompido após a implantação no ambiente de preparo e solicitará que o usuário execute a ação.
               * **`Now`** - Implanta para produção imediatamente, concluindo efetivamente o pipeline.
               * **Data** - Permite que o usuário programe o horário em que a implantação deverá ser concluída.
               * **Parar Execução** - Anula a implantação para produção.

           >[!TIP]
           >
           >Consulte [Implantação do código](/help/using/code-deployment.md) para saber como programar a implantação ou executar o pipeline imediatamente.

            * **Usar a Supervisão do CSE** - Se essa opção for selecionada, um CSE (Engenheiro de Sucesso do Cliente) será contratado para iniciar a implantação real. Ao criar ou editar um pipeline quando essa opção estiver habilitada, a função **Gerente de implantação** terá as seguintes opções.

               * **Qualquer CSE** - Permite que qualquer CSE disponível inicie a implantação.
               * **Meu CSE** - Permite que somente o CSE específico atribuído ao cliente inicie a implantação. Essa opção também se aplica ao CSE designado como substituto se o CSE atribuído não estiver disponível.

           ![Opções de implantação de produção](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configuração do Dispatcher** - Defina a configuração do Dispatcher para seu ambiente de produção. As opções são as mesmas do ambiente de preparo.

1. Clique em **Continuar** para avançar até a guia **Teste de preparo**, onde é possível configurar o teste de desempenho do AEM Sites e do AEM Assets, dependendo das licenças de produto que você possui.

   >[!TIP]
   >
   >Consulte [Teste de qualidade do código](/help/using/code-quality-testing.md#performance-testing) para obter mais detalhes sobre as opções disponíveis na guia **Teste de preparo**.

   1. Na seção **Entrega de conteúdo de sites/Peso de carga distribuído**, configure o Teste de desempenho do site com base na ponderação de solicitações de página entre três conjuntos de páginas. Você pode ativar ou desativar os conjuntos de páginas conforme necessário.

      * **Páginas populares ativas**
      * **Outras páginas ativas**
      * **Novas páginas**

      ![Peso de carregamento dos sites](/help/assets/configure-pipelines/add-prod5.png)

   1. Na seção **Distribuição de teste de desempenho de ativos**, você define a distribuição de teste de imagens e PDFs, bem como de seus próprios ativos de teste.

      * **Imagens** - Use o controle deslizante para ajustar a divisão do teste entre imagens e PDFs.
      * **PDF** - Use o controle deslizante para ajustar a divisão do teste entre imagens e PDFs.

      * Defina seus próprios ativos personalizados fazendo upload deles.

         1. **FORMATO** - Escolha se o ativo personalizado é um PDF de uma imagem.
         1. **NOME DE ARQUIVO** - Use o botão do navegador de arquivos para selecionar uma imagem de sua máquina local.
         1. **Adicionar arquivo de teste** - Clique para fazer upload do ativo selecionado.

      ![Distribuição de testes de ativos](/help/assets/configure-pipelines/add-prod6.png)

1. Clique em **Salvar** para concluir a adição do pipeline de produção.

## Próximas etapas {#the-next-steps}

Depois de configurar o pipeline, você implanta seu código. Consulte [Implantação de código](/help/using/code-deployment.md) para obter mais detalhes.

## Tutorial em vídeo {#video-tutorial-one}

Este vídeo fornece uma visão geral do processo de criação de pipeline, que é detalhado neste documento.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)
