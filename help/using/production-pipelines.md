---
title: Configuração de pipeline de produção
description: Saiba como usar o Cloud Manager para criar e configurar pipelines de produção para implantar seu código.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 99325c28c379103db2ba4c19bb6d206849c6e126
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 0%

---


# Configuração de pipeline de produção {#configuring-production-pipelines}

Saiba como usar o Cloud Manager para criar e configurar pipelines de produção para implantar seu código. se você quiser ter uma visão geral mais conceitual de como os pipelines funcionam no Cloud Manager, consulte o documento [Pipelines de CI/CD.](/help/overview/ci-cd-pipelines.md)

## Visão geral {#overview}

Usar o **Configurações de pipeline** bloco em [!UICONTROL Cloud Manager] você pode criar dois tipos diferentes de pipelines.

* **Pipelines de produção** - Um pipeline de produção é um pipeline criado especificamente com uma série de etapas orquestradas para levar o código fonte do seu repositório Git até a produção.
* **Pipelines de não produção** - Um pipeline não relacionado à produção serve principalmente para executar verificações de qualidade de código ou implantar o código-fonte em um ambiente de desenvolvimento.

Este documento se concentra em pipelines de produção. Para obter detalhes sobre como configurar pipelines de não produção, consulte o documento [Configuração de pipeline de não produção.](/help/using/non-production-pipelines.md)

O **Gerenciador de implantação** é responsável pela configuração do pipeline. A configuração do pipeline consiste em:

1. Definição do acionador que iniciará o pipeline.
1. Definição dos parâmetros que controlam a implantação de produção.
1. Configuração dos parâmetros de teste de desempenho.

>[!NOTE]
>
>Um pipeline não pode ser configurado até que seu repositório Git associado tenha pelo menos uma ramificação e [configuração do programa](/help/getting-started/program-setup.md) for concluído.

## Tutorial em vídeo {#video-tutorial-one}

Este vídeo fornece uma visão geral do processo de criação de pipeline, que é detalhado neste documento.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Adicionar um novo pipeline de produção {#adding-production-pipeline}

Depois de usar a variável [!UICONTROL Cloud Manager] Para configurar seu programa e ter pelo menos um ambiente, você está pronto para adicionar um pipeline de produção.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o **Pipelines** do cartão **Visão geral do programa** e clique em **+Adicionar** e selecione **Adicionar pipeline de produção**.

   ![Adicionar um pipeline de produção](/help/assets/configure-pipelines/add-prod1.png)

1. O **Adicionar pipeline de produção** a caixa de diálogo é aberta para o **Configuração** , onde várias opções do pipeline devem ser definidas. Essas opções são agrupadas em seções que podem ser recolhidas e são descritas nas etapas a seguir.

   1. Forneça um nome descritivo para o pipeline na **Nome do pipeline** campo.

   1. Em **Código fonte** , você define onde o pipeline recupera o código que processará.

      * **Repositório** - Essa opção define de qual Git repo o pipeline deve recuperar o código.
      >[!TIP]
      >
      >Consulte o documento [Configuração do programa](/help/getting-started/program-setup.md) para saber como adicionar e gerenciar repositórios no Cloud Manager.

      * **Ramificação Git** - Essa opção define de qual ramificação o pipeline selecionado deve recuperar o código.
      * **Localização do código** - Essa opção define o caminho na ramificação do acordo de recompra selecionado a partir do qual o pipeline deve recuperar o código.

      ![Definir acordos de recompra para o pipeline](/help/assets/configure-pipelines/add-prod2.png)

   1. Em **Ambientes** , você define o que aciona uma implantação e como ela deve ser implantada por ambiente.

      1. No **ESTÁGIO** , é possível definir como o pipeline é implantado em seu ambiente de preparo.

         * **Acionador da implantação** - Você tem as seguintes opções para definir os acionadores de implantação para iniciar o pipeline.

            * **Manual** - Use essa opção para iniciar manualmente o pipeline usando a interface do usuário do Cloud Manager.
            * **Nas alterações no Git** - Essas opções iniciam o pipeline de CI/CD sempre que os commits são adicionados à ramificação git configurada. Com essa opção, ainda é possível iniciar o pipeline manualmente, conforme necessário.
         * **Comportamento de falhas importantes da métrica** - Durante a configuração ou edição do pipeline, o Gerenciador de implantação tem a opção de definir o comportamento do pipeline quando uma falha importante for encontrada em qualquer uma das portas de qualidade. As opções disponíveis são:

            * **Perguntar sempre** - Esta é a configuração padrão e requer intervenção manual em qualquer falha importante.
            * **Falhar imediatamente** - Se selecionado, o pipeline será cancelado sempre que ocorrer uma falha importante. Isso é basicamente emular um usuário que rejeita manualmente cada falha.
            * **Continuar imediatamente** - Se selecionado, o pipeline continuará automaticamente sempre que ocorrer uma falha importante. Isso é basicamente emular um usuário que aprova manualmente cada falha.

         ![Acionador de implantação](/help/assets/configure-pipelines/add-prod3.png)

         * **Opções de implantação** - Você pode acelerar determinadas tarefas de implantação.

            * **Aprovar após implantação do estágio** - Essa aprovação ocorre após a implantação no ambiente de preparo antes da realização de qualquer teste. Caso contrário, a aprovação ocorre antes da implantação de produção, que é feita após a conclusão de todos os testes.

            * **Ignorar alterações no Balanceador de Carga** - Não são efetuadas alterações ao balanceador de carga.

         ![Opções de implantação de armazenamento temporário](/help/assets/configure-pipelines/add-prod4.png)

         * **Configuração do Dispatcher** - O **Gerenciador de implantação** pode configurar um conjunto de caminhos de conteúdo que serão invalidados ou liberados do cache do Dispatcher AEM quando um pipeline for executado. Essas ações de cache serão executadas como parte da etapa do pipeline de implantação, logo após a implantação de qualquer pacote de conteúdo. Essas configurações usam o comportamento padrão AEM Dispatcher. Para configurar:

            1. Em **CAMINHO** forneça um caminho de conteúdo.
            1. Em **TIPO**, selecione a ação a ser tomada nesse caminho.
            * **Liberar** - Execute uma invalidação de cache, de modo semelhante a quando o conteúdo é ativado de uma instância de criação para uma instância de publicação.
            * **Invalidar** - Executa uma exclusão de cache.
            1. Clique em **Adicionar caminho** para adicionar o caminho especificado. Você pode adicionar até 100 caminhos por ambiente.

         ![Configuração do Dispatcher](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >Em geral, o uso da ação de invalidação é preferível, mas pode haver casos em que a liberação é necessária, especialmente ao usar AEM bibliotecas de clientes do HTML.

      1. No **PRODUÇÃO** , é possível definir como o pipeline é implantado em seu ambiente de produção.

         * **Opções de implantação** - Você pode definir os parâmetros que controlam a implantação de produção.

            * **Usar Aprovação Ao Vivo** - Uma implantação deve ser aprovada manualmente por um usuário com a variável **Proprietário da empresa**, **Gerenciador de projetos** ou **Gerenciador de implantação** função por meio da [!UICONTROL Cloud Manager] IU.
            * **Programado** - Essa opção interrompe o pipeline antes da implantação de produção para permitir que ele seja agendado. Se essa opção estiver selecionada, o pipeline será interrompido após a implantação no ambiente de preparo e solicitará que o usuário execute a ação.
               * **Agora** - Essa opção é implantada na produção imediatamente, concluindo efetivamente o pipeline.
               * **Data** - Essa opção permite que o usuário agende um horário em que a implantação deve ser concluída.
               * **Parar Execução** - Essa opção aborta a implantação na produção.

            >[!TIP]
            >
            >Consulte o documento [Implantação do código,](/help/using/code-deployment.md) para saber como definir o agendamento de implantação ou executar o pipeline imediatamente.

            * **Usar a visão geral do caso** - Se essa opção for selecionada, um CSE será engajado para realmente iniciar a implantação. Ao criar ou editar um pipeline quando essa opção estiver ativada, a função **Gerenciador de implantação** tem as seguintes opções.

               * **Qualquer caso** - Essa opção permite que qualquer CSE disponível inicie a implantação.
               * **Meu CSE** - Essa opção permite que somente o CSE específico atribuído ao cliente inicie a implantação. Isso também se aplica ao backup designado do CSE se o CSE atribuído não estiver disponível.

            ![Opções de implantação de produção](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configuração do Dispatcher** - Defina a configuração do dispatcher para o ambiente de produção. As opções são as mesmas do ambiente de preparo.











1. Clique em **Continuar** para avançar para a **Teste de preparo** , onde é possível configurar o Teste de desempenho do AEM Sites e AEM Assets, dependendo de quais produtos você licenciou.

   >[!TIP]
   >
   >Consulte o documento [Teste de qualidade do código](/help/using/code-quality-testing.md#performance-testing) para obter mais detalhes sobre as opções disponíveis na **Teste de preparo** guia .

   1. Em **Entrega de conteúdo de sites/Peso de carga distribuído** , você define como o teste de desempenho de sites é configurado com base na ponderação de solicitações de página entre os três conjuntos de páginas, que podem ser ativadas ou desativadas.

      * **Páginas em tempo real populares**
      * **Outras páginas em tempo real**
      * **Novas páginas**

      ![Peso de carregamento dos sites](/help/assets/configure-pipelines/add-prod5.png)

   1. Em **Distribuição de teste de desempenho de ativos** , você define a distribuição de teste de imagens e PDF, bem como seus próprios ativos de teste.

      * **Imagens** - Ajuste o controle deslizante para ajustar a divisão do teste entre imagens e PDF.
      * **PDF** - Ajuste o controle deslizante para ajustar a divisão do teste entre imagens e PDF.

      * Defina seus próprios ativos personalizados fazendo upload deles.

         1. **FORMATO** - Escolha se o ativo personalizado é um PDF de uma imagem.
         1. **NOME DO ARQUIVO** - Use o botão do navegador de arquivos para selecionar uma imagem de sua máquina local.
         1. **Adicionar arquivo de teste** - Clique em para fazer upload do ativo selecionado.

      ![Distribuição de teste de ativos](/help/assets/configure-pipelines/add-prod6.png)



1. Clique em **Salvar** para concluir a adição do pipeline de produção.

## Próximas etapas {#the-next-steps}

Depois de configurar o pipeline, é necessário implantar seu código. Consulte o documento [Implantação do código](/help/using/code-deployment.md) para obter mais detalhes.
