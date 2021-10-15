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
source-git-commit: 973fec504cd5f35435b10e3d1d28f3ba20ff4ab9
workflow-type: tm+mt
source-wordcount: '1478'
ht-degree: 1%

---

# Configurar o pipeline de CI/CD {#configure-your-ci-cd-pipeline}

>[!NOTE]
>Para saber como configurar o pipeline de CI/CD para o Cloud Manager AEM as a Cloud Service, consulte [aqui](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager).

A página a seguir explica como configurar o **Pipeline**. Para analisar mais informações conceituais sobre como o pipeline funciona, consulte a [Visão geral do pipeline de CI/CD](ci-cd-pipeline.md).

## Tutorial em vídeo {#video-tutorial-one}

### Configuração do pipeline no Cloud Manager {#config-pipeline-video}

A configuração do pipeline de produção de CI/CD define o acionador que iniciará o pipeline, parâmetros que controlam a implantação de produção e parâmetros de teste de desempenho.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)


## Como entender o fluxo {#understanding-the-flow}

Você pode configurar o pipeline no bloco **Configurações de pipeline** na interface do usuário do [!UICONTROL Cloud Manager].

O Gerenciador de implantação é responsável pela configuração do pipeline. Ao fazer isso, primeiro selecione uma ramificação do **Repositório Git**. A configuração do pipeline consiste em:

* definindo o acionador que iniciará o pipeline.
* definição dos parâmetros que controlam a implantação de produção.
* configuração dos parâmetros de teste de desempenho.

## Configuração do pipeline {#setting-up-the-pipeline}

>[!CAUTION]
>
>O pipeline não pode ser configurado até que o repositório Git tenha pelo menos uma ramificação e [Configuração do Programa](setting-up-program.md) seja concluído.

Antes de começar a implantar seu código, você deve definir as configurações de pipeline do [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Você pode alterar as configurações do pipeline após a configuração inicial.

## Adicionar um novo pipeline de produção da placa de pipeline {#adding-production-pipeline}

Depois de configurar seu programa e ter pelo menos um ambiente usando a interface [!UICONTROL Cloud Manager], você estará pronto para adicionar um pipeline de produção.

Siga estas etapas para configurar o comportamento e as preferências do pipeline de produção:

1. Navegue até o cartão **Pipelines** da página **Visão geral do programa**.

1. Clique em **+Adicionar** e selecione **Adicionar pipeline de produção**.

   ![](/help/using/assets/configure-pipelines/add-prod1.png)

1. **A caixa de diálogo Adicionar** pipeline de produção é exibida.

   1. Insira o nome do pipeline. Você pode escolher o **Repository** e o **Git Branch**.

      ![](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Você pode configurar **Acionador de Implantação** e **Comportamento de Falha Importante** em **Opções de Implantação**.

      ![](/help/using/assets/configure-pipelines/add-prod3.png)


      Você pode definir o acionador para iniciar o pipeline:

      * **Manual**  - uso da interface do usuário para iniciar manualmente o pipeline.
      * **Em alterações no Git**  - inicia o pipeline de CI/CD sempre que há confirmações adicionadas à ramificação git configurada. Mesmo que você selecione essa opção, sempre poderá iniciar o pipeline manualmente.

         >[!NOTE]
         >Durante a configuração ou edição do pipeline, o Gerenciador de implantação tem a opção de definir o comportamento do pipeline quando uma falha importante for encontrada em qualquer uma das portas de qualidade.
      Isso é útil para clientes que desejam processos mais automatizados. As opções disponíveis são:

      * **Perguntar sempre**  - Essa é a configuração padrão e requer intervenção manual em qualquer falha importante.
      * **Cancelar imediatamente**  - se selecionado, o pipeline será cancelado sempre que ocorrer uma falha importante. Isso é basicamente emular um usuário que rejeita manualmente cada falha.
      * **Aprovar imediatamente**  - Se selecionado, o pipeline continuará automaticamente sempre que ocorrer uma falha importante. Isso é basicamente emular um usuário que aprova manualmente cada falha.
   1. Selecione as **Opções de Implantação**.

      ![](/help/using/assets/configure-pipelines/add-prod4.png)

      * **Aprovar após a** Implantação do Estágio funciona de forma semelhante à aprovação antes da implantação de produção, mas ocorre imediatamente após a etapa de implantação do estágio, ou seja, antes que qualquer teste seja feito, em comparação com a aprovação antes da implantação de produção, que é feita após a conclusão de todos os testes.

      * **Ignorar Balanceador de Carga**
   1. Selecione **Configurações do Dispatcher** para Preparo. Insira o caminho, selecione a ação de **Type** e clique em **Adicionar caminho**. Você pode especificar até 100 caminhos por ambiente.

      ![](/help/using/assets/configure-pipelines/dispatcher-stage.png)

   1. Selecione **Opções de Implantação** para Produção. Agora você define os parâmetros que controlam a implantação de produção. As três opções disponíveis são as seguintes:

      * **Uso de Aprovação em tempo real**  - uma implantação deve ser aprovada manualmente por um proprietário de negócios, gerente de projeto ou gerente de implantação por meio da  [!UICONTROL Cloud Manager] interface do usuário.
      * **Use a Supervisão de CSE**  - Um CSE é engajado para realmente iniciar a implantação. Durante a configuração do pipeline ou edite quando o CSE Oversight estiver ativado, o Gerenciador de implantação tem a opção de selecionar:

      * **Qualquer caso**: refere-se a qualquer caso disponível
      * **Meu caso**: se refere a um CSE específico atribuído ao cliente ou ao backup, se o CSE estiver fora do escritório

      * **Scheduled**  - essa opção permite que o usuário habilite a implantação de produção agendada.

         >[!NOTE]
         >Se a opção **Scheduled** estiver selecionada, você poderá agendar a implantação de produção para o pipeline **depois de** a implantação do palco (e **Use GoLive Approval**, se isso tiver sido ativado) para aguardar a definição de um agendamento. O usuário também pode optar por executar a implantação de produção imediatamente.
         >
         >Consulte [Implante o Código](deploying-code.md) para definir o agendamento de implantação ou executar a produção imediatamente.
   1. Configure as **Configurações do Dispatcher** para Produção. Insira o caminho, selecione a ação de **Type** e clique em **Adicionar caminho**. Você pode especificar até 100 caminhos por ambiente.

      ![](/help/using/assets/configure-pipelines/dispatcher-prod.png)

      Como um Gerenciador de implantação, você tem a oportunidade de configurar um conjunto de caminhos de conteúdo que serão **invalidados** ou **liberados** do cache do Dispatcher AEM para instâncias de publicação, enquanto configura ou edita o pipeline.

      Você pode configurar um conjunto separado de caminhos para a implantação de Preparo e Produção. Se configuradas, essas ações de cache serão executadas como parte da etapa do pipeline de implantação, logo após a implantação de qualquer pacote de conteúdo. Essas configurações usam o comportamento padrão AEM do Dispatcher - a invalidação executa uma invalidação de cache, de modo semelhante a quando o conteúdo é ativado do autor para publicação; flush executa uma exclusão de cache.

      Em geral, o uso da ação de invalidação é preferível, mas pode haver casos em que a liberação é necessária, especialmente ao usar AEM bibliotecas de clientes do HTML.

      >[!NOTE]
      >
      >Consulte [Visão geral do Dispatcher](dispatcher-configurations.md) para obter mais informações sobre o armazenamento em cache do Dispatcher.





1. Clique em **Continuar** depois de selecionar todas as opções.

1. Selecione suas opções na etapa **Teste de preparo**. Você pode configurar os *AEM Sites* e *AEM Assets* Testes de Desempenho, dependendo dos produtos que você licenciou. Consulte [Teste de desempenho](understand-your-test-results.md#performance-testing) para obter mais detalhes.

   1. Selecione suas opções de **Entrega de conteúdo de sites/Peso de carga distribuído**. Consulte [AEM Sites em Teste de desempenho](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-sites) para obter mais detalhes.

      ![](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Selecione as opções de **Distribuição de teste de desempenho de ativos**. Consulte [AEM Assets em Teste de desempenho](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-assets) para obter mais detalhes.

      ![](/help/using/assets/configure-pipelines/add-prod6.png)

1. Clique em **Save** para concluir a adição do pipeline de produção.

### Edição de um pipeline de produção {#editing-prod-pipeline}

É possível editar as configurações de pipeline na página **Visão geral do programa**.

Siga as etapas abaixo para editar o pipeline configurado:

1. Navegue até o cartão **Pipelines** da página **Visão geral do programa**.

1. Clique em **...** no cartão **Pipelines** e clique em **Editar**, conforme mostrado na figura abaixo.

   ![](/help/using/assets/configure-pipelines/edit-prod1.png)

1. A caixa de diálogo **Editar pipeline de produção** é exibida.

   1. A guia **Configuração** permite atualizar o **Nome do pipeline**, **Repositório**, **Ramificação Git**, **Acionador de implantação**, **Comportamento de falha de métricas importantes** , **Opções de Implantação** e **Configurações do Dispatcher**.

      >[!NOTE]
      >Consulte [Adicionar e gerenciar repositórios](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) para saber como adicionar e gerenciar repositórios no Cloud Manager.


   1. A guia **Teste de preparo** fornece uma opção para selecionar novamente suas opções de **Entrega de conteúdo de sites/Peso de carga distribuído** e **Distribuição de teste de desempenho de ativos**.

1. Clique em **Atualizar** depois de concluir a edição do pipeline.

## Pipelines somente para não-produção e qualidade de código

Além do pipeline principal que é implantado na fase e na produção, os clientes podem configurar pipelines adicionais, conhecidos como **Non-Production Pipelines**. Esses pipelines sempre executam as etapas de criação e qualidade do código. Como opção, também podem implantar no ambiente do Adobe Managed Services.

## Tutorial em vídeo {#video-tutorial-two}

### Pipelines do Cloud Manager que não são de produção e qualidade de código {#non-prod-video}

CI/CD Os pipelines de não produção são divididos em duas categorias, pipelines de qualidade de código e pipelines de implantação. O código de pipelines de qualidade todos os códigos de uma ramificação Git para criar e ser avaliado em relação à verificação de qualidade do código do Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

### Adicionar um pipeline de não produção {#add-non-production-pipeline}

Na tela inicial, esses pipelines são listados em um novo cartão:

1. Acesse o cartão **Pipelines** da tela inicial do Cloud Manager. Clique em **+Adicionar** e selecione **Adicionar pipeline de não produção**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. **A caixa de diálogo Adicionar**  pipeline de não produção é exibida. Selecione o tipo de pipeline que deseja criar, seja **Pipeline de Qualidade de Código** ou **Pipeline de Implantação**.

   Além disso, você também pode configurar **Acionador de implantação** e **Comportamento de falha importante** em **Opções de implantação**. Clique em **Continuar**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add2.png)


1. O pipeline de não produção recém-criado agora é exibido no cartão **Pipelines**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add4.png)


   O pipeline é mostrado no cartão na tela inicial com três ações, conforme mostrado abaixo:

   * **Adicionar**  - permite adicionar um novo pipeline.
   * **Acessar informações do acordo de recompra**  - permite que o usuário obtenha as informações necessárias para acessar o repositório Git do Cloud Manager.
   * **Saiba mais**  - navegue para entender o recurso de documentação do pipeline de CI/CD.

### Edição de um pipeline de não produção {#editing-nonprod-pipeline}

Você pode editar as configurações de pipeline no cartão **Pipelines** da página **Visão geral do programa**.

Siga as etapas abaixo para editar o pipeline de não produção configurado:

1. Navegue até o cartão **Pipelines** da página **Visão geral do programa**.

1. Selecione o pipeline de não produção e clique em **...**. Clique em **Editar**, conforme mostrado na figura abaixo.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit1.png)

1. A caixa de diálogo **Editar pipeline de produção** é exibida e permite atualizar o **Nome do pipeline**, **Repositório**, **Ramificação Git**, **Acionador de implantação** e **Comportamento de falha de métricas importantes**.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit2.png)

   >[!NOTE]
   >Consulte [Adicionar e gerenciar repositórios](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) para saber como adicionar e gerenciar repositórios no Cloud Manager.


1. Clique em **Atualizar** depois de concluir a edição do pipeline de não produção.


## Próximas etapas {#the-next-steps}

Depois de configurar o pipeline, é necessário implantar seu código.

Consulte [Implantar o código](deploying-code.md) para obter mais detalhes.
