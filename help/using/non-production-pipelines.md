---
title: Configuração de pipelines de não produção
description: Saiba como usar o Cloud Manager para criar e configurar pipelines de não produção para implantar seu código.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 567a16a032bf80451b5e8ba4e3d842cb617a615f
workflow-type: ht
source-wordcount: '600'
ht-degree: 100%

---

# Configuração de pipelines de não produção {#configuring-non-production-pipelines}

Saiba como usar o Cloud Manager para criar e configurar pipelines de não produção para implantar seu código. Se desejar ter uma visão geral mais conceitual de como os pipelines funcionam no Cloud Manager, consulte o documento [Pipelines de CI/CD.](/help/overview/ci-cd-pipelines.md)

## Visão geral {#overview}

Ao usar o bloco **Pipelines** no [!UICONTROL Cloud Manager], o **Gerenciador de implantação** pode criar dois tipos diferentes de pipelines.

* **Pipelines de produção** - um pipeline de produção é concebido para fins específicos e é constituído por uma série de etapas orquestradas, com o objetivo de levar o código-fonte até à produção.
* **Pipelines de não produção** - um pipeline não relacionado à produção serve principalmente para executar verificações de qualidade de código ou implantar o código-fonte em um ambiente de desenvolvimento.

Este documento se concentra em pipelines de não produção. Para obter detalhes sobre como configurar pipelines de produção, consulte o documento [Configuração de pipelines de produção.](/help/using/production-pipelines.md)

Existem dois tipos de pipelines de não produção:

* **Pipelines de qualidade do código** - executam verificações de qualidade de código em uma ramificação do Git e executam as etapas de criação e qualidade de código.
* **Pipelines de implantação** - além de executar as etapas de criação e qualidade do código, como os pipelines de qualidade de código, esses pipelines implantam o código em um ambiente de não produção.

>[!NOTE]
>
>Um pipeline não pode ser configurado até que seu repositório Git associado tenha pelo menos uma ramificação e a [configuração do programa](/help/getting-started/program-setup.md) seja concluída. Consulte o documento [Repositórios do Cloud Manager](/help/managing-code/repositories.md) para saber como adicionar e gerenciar repositórios no Cloud Manager.

## Tutorial em vídeo {#video-tutorial}

Este vídeo fornece uma visão geral do processo de criação de pipeline, que é detalhado neste documento.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

## Adicionar um pipeline de não produção {#add-non-production-pipeline}

Depois de configurar seu programa e ter pelo menos um ambiente que utiliza a interface do Cloud Manager, você estará pronto para adicionar um pipeline de não produção seguindo essas etapas.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selecione a organização e o programa apropriados.

1. Acesse o cartão Pipelines na tela inicial do Cloud Manager. Clique em **Adicionar** e selecione **Adicionar pipeline de não produção**.

   ![Adicionar pipeline de não produção](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Na guia **Configuração** da caixa de diálogo **Adicionar pipeline de não produção**, selecione o tipo de pipeline que deseja criar, um **pipeline de qualidade de código** ou **pipeline de implantação**.

   ![Escolha o tipo de pipeline](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Forneça uma descrição para o pipeline no campo **Nome do pipeline de não produção**.

1. Se você optou por adicionar um **pipeline de implantação**, selecione o ambiente de implantação de destino na lista suspensa **Ambientes de implantação elegíveis**.

1. Forneça o repositório onde o pipeline deve recuperar o código.

   * **Repositório** - essas opções definem a partir de qual repositório Git o pipeline deve recuperar o código.
   * **Ramificação Git** - essa opção define de qual ramificação o pipeline selecionado deve recuperar o código.

1. Defina suas opções de implantação.

   1. Em **Acionador de implantação**, defina qual evento ativa o pipeline.

      * **Manual** - use essa opção para iniciar manualmente o pipeline.
      * **Sobre alterações do Git** - essas opções iniciam o pipeline sempre que as confirmações forem adicionadas à ramificação Git configurada. Com essa opção, ainda é possível iniciar o pipeline manualmente, conforme necessário.
   1. Para pipelines de implantação, em **Comportamento de falhas de métricas importantes**, defina o comportamento do pipeline quando uma falha importante for encontrada em qualquer uma das portas de qualidade.

      * **Pergunte sempre** - é a configuração padrão e requer intervenção manual em qualquer falha importante.
      * **Falha imediata** - Se selecionada, o pipeline será cancelado sempre que ocorrer uma falha importante. É basicamente semelhante a um usuário que rejeita manualmente cada falha.
      * **Continuar imediatamente** - Se essa opção for selecionada, o pipeline continuará automaticamente sempre que ocorrer uma falha importante. É basicamente semelhante a um usuário que aprova manualmente cada falha.


1. Clique em **Salvar** para salvar o pipeline.

## Próximas etapas {#the-next-steps}

Depois de configurar o pipeline, é necessário implantar o código. Consulte o documento [Implantação do código](/help/using/code-deployment.md) para obter mais detalhes.
