---
title: Configuração de pipeline de não produção
description: Saiba como usar o Cloud Manager para criar e configurar pipelines de não produção para implantar seu código.
source-git-commit: 205113735cc743e11e140b1161413002844f5b79
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---


# Configuração de pipeline de não produção {#configuring-non-production-pipelines}

Saiba como usar o Cloud Manager para criar e configurar pipelines de não produção para implantar seu código. se você quiser ter uma visão geral mais conceitual de como os pipelines funcionam no Cloud Manager, consulte a [Documentação de visão geral do pipeline de CI/CD.](ci-cd-pipeline.md)

>[!NOTE]
>
>Para saber como configurar pipelines de CI/CD para o Cloud Manager AEM as a Cloud Service, consulte [a documentação do AEMaaCS.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html#using-cloud-manager)

## Visão geral {#understanding-the-flow}

O **Gerenciador de implantação** A função é responsável pela configuração do pipeline usando o **Pipelines** no bloco de [!UICONTROL Cloud Manager] IU.

Você pode criar dois tipos diferentes de pipelines.

* **Pipelines de produção** - Um gasoduto de produção é um oleoduto concebido para fins específicos, constituído por uma série de etapas orquestradas, com o objetivo de levar todo o código-fonte até à produção.
* **Pipelines de não produção** - Um pipeline não relacionado à produção serve principalmente para executar verificações de qualidade de código ou implantar o código-fonte em um ambiente de desenvolvimento.

Este documento se concentra em pipelines de não produção. Para obter detalhes sobre como configurar pipelines de não produção, consulte o documento [Configuração de pipeline de não produção.](configuring-non-production-pipelines.md)

Existem dois tipos de gasodutos não relacionados à produção:

* **Pipelines de qualidade do código** - Esses executam verificações de qualidade de código no código em uma ramificação git e executa as etapas de qualidade de código e criação.
* **Pipelines de implantação** - Além de executar as etapas de criação e qualidade do código, como os pipelines de qualidade do código, esses pipelines implantam o código em um ambiente não relacionado à produção.

>[!NOTE]
>
>Um pipeline não pode ser configurado até que seu repositório Git associado tenha pelo menos uma ramificação e [configuração do programa](setting-up-program.md) for concluído. Consulte [Adicionar e gerenciar repositórios](cloud-manager-repositories.md) para saber como adicionar e gerenciar repositórios no Cloud Manager.

## Tutorial em vídeo {#video-tutorial-two}

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

## Adicionar um pipeline de não produção {#add-non-production-pipeline}

Depois de configurar seu programa e ter pelo menos um ambiente usando a interface do usuário do Cloud Manager, você estará pronto para adicionar um pipeline de não produção seguindo essas etapas.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selecione a organização e o programa apropriados.

1. Acesse o cartão Pipelines na tela inicial do Cloud Manager. Clique em **Adicionar** e selecione **Adicionar pipeline de não-produção**.

   ![Adicionar pipeline de não produção](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. No **Configuração** da guia **Adicionar pipeline de não-produção** , selecione o tipo de pipeline que deseja criar, um **Pipeline de qualidade do código** ou **Pipeline de implantação**.


   ![Escolha o tipo de pipeline](/help/using/assets/configure-pipelines/add-non-production-pipeline.png)

1. Forneça uma descrição para o pipeline na **Nome do pipeline de não produção** campo.

1. Se você optou por adicionar um **Pipeline de implantação**, selecione o ambiente de implantação do target no **Ambientes de implantação qualificados** lista suspensa.

1. Forneça o repositório onde o pipeline deve recuperar o código.

   * **Repositório** - Essas opções definem a partir de qual Git repo o pipeline deve recuperar o código.
   * **Ramificação Git** - Essa opção define de qual ramificação o pipeline selecionado deve recuperar o código.

1. Defina suas opções de implantação.

   1. Em **Acionador da implantação**, defina qual evento ativa o pipeline.

      * **Manual** - Use essa opção para iniciar manualmente o pipeline.
      * **Nas alterações no Git** - Essas opções iniciam o pipeline sempre que as confirmações forem adicionadas à ramificação git configurada. Com essa opção, ainda é possível iniciar o pipeline manualmente, conforme necessário.
   1. Em **Comportamento de falhas importantes da métrica**, defina o comportamento do pipeline quando uma falha importante for encontrada em qualquer uma das portas de qualidade.

      * **Perguntar sempre** - Esta é a configuração padrão e requer intervenção manual em qualquer falha importante.
      * **Falhar imediatamente** - Se selecionado, o pipeline será cancelado sempre que ocorrer uma falha importante. Isso é basicamente emular um usuário que rejeita manualmente cada falha.
      * **Continuar imediatamente** - Se selecionado, o pipeline continuará automaticamente sempre que ocorrer uma falha importante. Isso é basicamente emular um usuário que aprova manualmente cada falha.


1. Clique em **Salvar** para salvar o pipeline.

## Próximas etapas {#the-next-steps}

Depois de configurar o pipeline, é necessário implantar seu código.

Consulte o documento [Implantar o código](deploying-code.md) para obter mais detalhes.
