---
title: Configurar o pipeline de CI/CD
seo-title: Configure your CI/CD Pipeline
description: Siga esta página para configurar suas configurações de pipeline no Cloud Manager.
seo-description: Before you start to deploy your code, you must configure your pipeline settings from the AEM Cloud Manager.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 2be8f290b58fff2991f876c37dd1b499bc6c5352
workflow-type: tm+mt
source-wordcount: '1834'
ht-degree: 1%

---

# Configurar o pipeline de CI/CD {#configure-your-ci-cd-pipeline}

>[!NOTE]
>Para saber como configurar o pipeline de CI/CD para o Cloud Manager AEM as a Cloud Service, consulte [here](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager).

A página a seguir explica como configurar o **Pipeline**. Para analisar mais informações conceituais sobre como o pipeline funciona, consulte a [Visão geral do pipeline de CI/CD](ci-cd-pipeline.md).


## Como entender o fluxo {#understanding-the-flow}

Você pode configurar o pipeline no bloco **Configurações de pipeline** na interface do usuário do [!UICONTROL Cloud Manager].

O Gerenciador de implantação é responsável pela configuração do pipeline. Ao fazer isso, primeiro selecione uma ramificação da **Repositório Git**. A configuração do pipeline consiste em:

* definindo o acionador que iniciará o pipeline.
* definição dos parâmetros que controlam a implantação de produção.
* configuração dos parâmetros de teste de desempenho.

## Tutorial em vídeo {#video-tutorial-one}

### Configuração do pipeline no Cloud Manager {#config-pipeline-video}

A configuração do pipeline de produção de CI/CD define o acionador que iniciará o pipeline, parâmetros que controlam a implantação de produção e parâmetros de teste de desempenho.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Configuração do pipeline {#setting-up-the-pipeline}

>[!CAUTION]
>
>O pipeline não pode ser configurado até que o repositório Git tenha pelo menos uma ramificação e [Configuração do programa](setting-up-program.md) for concluído.

Antes de começar a implantar seu código, você deve definir as configurações de pipeline do [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Você pode alterar as configurações do pipeline após a configuração inicial.

### Adicionar um novo pipeline de produção da placa de pipeline {#adding-production-pipeline}

Depois de configurar seu programa e ter pelo menos um ambiente usando [!UICONTROL Cloud Manager] Interface do usuário do , você está pronto para adicionar um pipeline de produção.

Siga estas etapas para configurar o comportamento e as preferências do pipeline de produção:

1. Navegue até o **Pipelines** do cartão **Visão geral do programa** página.

1. Clique em **+Adicionar** e selecione **Adicionar pipeline de produção**.

   ![](/help/using/assets/configure-pipelines/add-prod1.png)

1. **Adicionar pipeline de produção** será exibida.

   1. Insira o **Nome do pipeline**. Você pode escolher a variável **Repositório** e **Ramificação Git**.

      ![](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Você pode configurar **Acionador da implantação** e **Comportamento de falhas importantes da métrica** from **Opções de implantação**.

      ![](/help/using/assets/configure-pipelines/add-prod3.png)


      Você pode atribuir os seguintes acionadores de implantação para iniciar o pipeline:

      * **Manual** - uso da interface do usuário para iniciar manualmente o pipeline.
      * **Nas alterações no Git** - inicia o pipeline de CI/CD sempre que há confirmações adicionadas à ramificação git configurada. Mesmo que você selecione essa opção, sempre poderá iniciar o pipeline manualmente.

      Durante a configuração ou edição do pipeline, o Gerenciador de implantação tem a opção de definir o comportamento do pipeline quando uma falha importante for encontrada em qualquer uma das portas de qualidade.

      Isso é útil para clientes que desejam processos mais automatizados. As opções disponíveis são:

      * **Perguntar sempre** - Esta é a configuração padrão e requer intervenção manual em qualquer falha importante.
      * **Falhar imediatamente** - Se selecionado, o pipeline será cancelado sempre que ocorrer uma falha importante. Isso é basicamente emular um usuário que rejeita manualmente cada falha.
      * **Continuar imediatamente** - Se selecionado, o pipeline continuará automaticamente sempre que ocorrer uma falha importante. Isso é basicamente emular um usuário que aprova manualmente cada falha.
   1. Selecione o **Opções de implantação**.

      ![](/help/using/assets/configure-pipelines/add-prod4.png)

      * **Aprovar após implantação do estágio** funciona de forma semelhante à aprovação antes da implantação de produção, mas ocorre imediatamente após a etapa de implantação do estágio, ou seja, antes que qualquer teste seja feito, em comparação com a aprovação antes da implantação de produção, que é feita após a conclusão de todos os testes.

      * **Ignorar alterações no Balanceador de Carga** ignora as alterações.
   1. Selecione o **Configuração do Dispatcher** para Estágio. Insira o caminho, selecione a ação de **Tipo** e clique em **Adicionar caminho**. Você pode especificar até 100 caminhos por ambiente.

      ![](/help/using/assets/configure-pipelines/dispatcher-stage.png)

   1. Selecione o **Opções de implantação** para produção. Agora você define os parâmetros que controlam a implantação de produção.

      ![](/help/using/assets/configure-pipelines/prod-deploymentoptions.png)

      As três opções disponíveis são as seguintes:

      * **Usar Aprovação Ao Vivo** - Uma implantação deve ser aprovada manualmente por um proprietário de negócios, gerente de projeto ou gerente de implantação por meio do [!UICONTROL Cloud Manager] IU.

      * **Programado** - Essa opção permite que o usuário habilite a implantação de produção agendada.

         >[!NOTE]
         >If **Programado** estiver selecionada, você poderá agendar a implantação de produção para o pipeline **after** a implantação do estágio (e **Usar aprovação de GoLive**, se isso tiver sido ativado) para aguardar a definição de um agendamento. O usuário também pode optar por executar a implantação de produção imediatamente.
         >
         >Consulte [Implantar o código](deploying-code.md), para definir o agendamento de implantação ou executar a produção imediatamente.

         * **Usar a visão geral do caso** - Um CSE está comprometido a realmente iniciar a implantação. Durante a configuração do pipeline ou edite quando o CSE Oversight estiver ativado, o Gerenciador de implantação tem a opção de selecionar:

            * **Qualquer caso**: refere-se a qualquer caso disponível
            * **Meu CSE**: se refere a um CSE específico atribuído ao cliente ou ao backup, se o CSE estiver fora do escritório
   1. Configure o **Configurações do Dispatcher** para produção. Insira o caminho, selecione a ação de **Tipo** e clique em **Adicionar caminho**. Você pode especificar até 100 caminhos por ambiente.

      ![](/help/using/assets/configure-pipelines/dispatcher-prod.png)

      Como um Gerenciador de implantação, você tem a oportunidade de configurar um conjunto de caminhos de conteúdo que **invalidado** ou **lavado** do cache do Dispatcher AEM para instâncias de publicação, ao configurar ou editar o pipeline.

      Você pode configurar um conjunto separado de caminhos para a implantação de Preparo e Produção. Se configuradas, essas ações de cache serão executadas como parte da etapa do pipeline de implantação, logo após a implantação de qualquer pacote de conteúdo. Essas configurações usam o comportamento padrão AEM do Dispatcher - a invalidação executa uma invalidação de cache, de modo semelhante a quando o conteúdo é ativado do autor para publicação; flush executa uma exclusão de cache.

      Em geral, o uso da ação de invalidação é preferível, mas pode haver casos em que a liberação é necessária, especialmente ao usar AEM bibliotecas de clientes do HTML.

      >[!NOTE]
      >
      >Consulte [Visão geral do Dispatcher](dispatcher-configurations.md) obtenha mais informações sobre o armazenamento em cache do Dispatcher.





1. Clique em **Continuar** depois de selecionar todas as opções.

1. Selecione suas opções no **Teste de preparo** etapa. Você pode configurar *AEM Sites* e *AEM Assets* Teste de desempenho, dependendo de quais produtos você licenciou. Consulte [Teste de desempenho](understand-your-test-results.md#performance-testing) para obter mais detalhes.

   1. Selecione suas opções em **Entrega de conteúdo de sites/Peso de carga distribuído**. Consulte [AEM Sites em testes de desempenho](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-sites) para obter mais detalhes.

      ![](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Selecione suas opções em **Distribuição de teste de desempenho de ativos**. Consulte [AEM Assets em testes de desempenho](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-assets) para obter mais detalhes.

      ![](/help/using/assets/configure-pipelines/add-prod6.png)

1. Clique em **Salvar** para concluir a adição do pipeline de produção.

### Edição de um pipeline de produção {#editing-prod-pipeline}

É possível editar as configurações de pipeline da variável **Visão geral do programa** página.

Siga as etapas abaixo para editar o pipeline configurado:

1. Navegar para **Pipelines** do cartão **Visão geral do programa** página.

1. Clique em **...** do **Pipelines** e clique em **Editar**, conforme mostrado na figura abaixo.

   ![](/help/using/assets/configure-pipelines/edit-prod1.png)

1. O **Editar pipeline de produção** será exibida.

   1. O **Configuração** permite atualizar a guia **Nome do pipeline**, **Repositório**, **Ramificação Git**, **Acionador da implantação**, **Comportamento de falha de métricas importantes**, **Opções de implantação** e **Configurações do Dispatcher**.

      >[!NOTE]
      >Consulte [Adicionar e gerenciar repositórios](/help/using/cloud-manager-repositories.md) para saber como adicionar e gerenciar repositórios no Cloud Manager.


   1. O **Teste de preparo** A guia fornece uma opção para reselecionar suas opções em **Entrega de conteúdo de sites/Peso de carga distribuído** e **Distribuição de teste de desempenho de ativos**.

1. Clique em **Atualizar** depois de concluir a edição do pipeline.

### Ações adicionais do pipeline de produção {#additional-prod-actions}

#### Execução de um pipeline de produção {#run-prod}

Você pode executar o pipeline de produção no cartão Pipelines :

1. Navegar para **Pipelines** do cartão **Visão geral do programa** página.

1. Clique em **...** do **Pipelines** e clique em **Executar**, conforme mostrado na figura abaixo.

   ![](/help/using/assets/configure-pipelines/prod-run.png)

#### Exclusão de um pipeline de produção {#delete-prod}

Você pode excluir o pipeline de produção do cartão Pipelines:

1. Navegar para **Pipelines** do cartão **Visão geral do programa** página.

1. Clique em **...** do **Pipelines** e clique em **Excluir**, conforme mostrado na figura abaixo.

   ![](/help/using/assets/configure-pipelines/prod-delete.png)

   >[!NOTE]
   >Um usuário na função Gerenciador de implantação agora pode excluir o pipeline de Produção de maneira automatizada por meio do **Excluir** na placa Pipeline.

## Pipelines somente para não-produção e qualidade de código

Para além do principal gasoduto de implantação e de produção, os clientes podem criar oleodutos adicionais, referidos como **Pipelines de não produção**. Esses pipelines sempre executam as etapas de criação e qualidade do código. Como opção, também podem implantar no ambiente do Adobe Managed Services.

## Tutorial em vídeo {#video-tutorial-two}

### Pipelines do Cloud Manager que não são de produção e qualidade de código {#non-prod-video}

CI/CD Os pipelines de não produção são divididos em duas categorias, pipelines de qualidade de código e pipelines de implantação. O código de pipelines de qualidade todos os códigos de uma ramificação Git para criar e ser avaliado em relação à verificação de qualidade do código do Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

### Adicionar um pipeline de não produção {#add-non-production-pipeline}

Na tela inicial, esses pipelines são listados em um novo cartão:

1. Acesse o **Pipelines** na tela inicial do Cloud Manager. Clique em **+Adicionar** e selecione **Adicionar pipeline de não-produção**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. **Adicionar pipeline de não-produção**  será exibida. Selecione o tipo de pipeline que deseja criar, **Pipeline de qualidade do código** ou **Pipeline de implantação**.

   Além disso, também é possível configurar **Acionador da implantação** e **Comportamento de falhas importantes da métrica** from **Opções de implantação**. Clique em **Continuar**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add2.png)


1. O pipeline de não produção recém-criado agora é exibido na variável **Pipelines** cartão.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add4.png)


   O pipeline é mostrado no cartão na tela inicial com três ações, conforme mostrado abaixo:

   * **Adicionar** - permite adicionar um novo pipeline.
   * **Acessar informações do repositório** - permite que o usuário obtenha as informações necessárias para acessar o repositório Git do Cloud Manager.
   * **Saiba mais** - navega para entender o recurso de documentação do pipeline de CI/CD.

### Edição de um pipeline de não produção {#editing-nonprod-pipeline}

É possível editar as configurações de pipeline da variável **Cartão de pipeline** from **Visão geral do programa** página.

Siga as etapas abaixo para editar o pipeline de não produção configurado:

1. Navegar para **Pipelines** do cartão **Visão geral do programa** página.

1. Selecione o pipeline de não produção e clique em **...**. Clique em **Editar**, conforme mostrado na figura abaixo.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit1.png)

1. O **Editar pipeline de produção** é exibida uma caixa de diálogo que permite atualizar a **Nome do pipeline**, **Repositório**, **Ramificação Git**, **Acionador da implantação** e **Comportamento de falha de métricas importantes**.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit2.png)

   >[!NOTE]
   >Consulte [Adicionar e gerenciar repositórios](/help/using/cloud-manager-repositories.md) para saber como adicionar e gerenciar repositórios no Cloud Manager.

   Você pode atribuir os seguintes acionadores de implantação para iniciar o pipeline:

   * **Manual** - uso da interface do usuário para iniciar manualmente o pipeline.
   * **Nas alterações no Git** - inicia o pipeline de CI/CD sempre que há confirmações adicionadas à ramificação git configurada. Mesmo que você selecione essa opção, sempre poderá iniciar o pipeline manualmente.

   Durante a configuração ou edição do pipeline, o Gerenciador de implantação tem a opção de definir o comportamento do pipeline quando uma falha importante for encontrada em qualquer uma das portas de qualidade. Isso é útil para clientes que desejam processos mais automatizados. As opções disponíveis são:

   * **Perguntar sempre** - Esta é a configuração padrão e requer intervenção manual em qualquer falha importante.
   * **Falhar imediatamente** - Se selecionado, o pipeline será cancelado sempre que ocorrer uma falha importante. Isso é basicamente emular um usuário que rejeita manualmente cada falha.
   * **Continuar imediatamente** - Se selecionado, o pipeline continuará automaticamente sempre que ocorrer uma falha importante. Isso é basicamente emular um usuário que aprova manualmente cada falha.


1. Clique em **Atualizar** depois de concluir a edição do pipeline de não produção.

### Ações adicionais do pipeline de não produção {#additional-nonprod-actions}

#### Execução de um pipeline de não produção {#run-nonprod}

Você pode executar o pipeline de produção no cartão Pipelines :

1. Navegar para **Pipelines** do cartão **Visão geral do programa** página.

1. Clique em **...** do **Pipelines** e clique em **Executar**, conforme mostrado na figura abaixo.

   ![](/help/using/assets/configure-pipelines/nonprod-run1.png)

#### Excluindo um pipeline de não produção {#delete-nonprod}

Você pode excluir o pipeline de produção do cartão Pipelines:

1. Navegar para **Pipelines** do cartão **Visão geral do programa** página.

1. Clique em **...** do **Pipelines** e clique em **Excluir**, conforme mostrado na figura abaixo.

   ![](/help/using/assets/configure-pipelines/nonprod-delete.png)


## Próximas etapas {#the-next-steps}

Depois de configurar o pipeline, é necessário implantar seu código.

Consulte [Implantar o código](deploying-code.md) para obter mais detalhes.
