---
title: Adicionar um pipeline de produção
description: Saiba como usar o Cloud Manager para criar e configurar pipelines de produção para implantar seu código.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 1209faf71edbd74cd87acfe24ec438b98ddd4a3a
workflow-type: ht
source-wordcount: '1249'
ht-degree: 100%

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

   ![Adicionar um pipeline de produção](/help/assets/configure-pipelines/add-prod1.png)

1. A caixa de diálogo **Adicionar pipeline de produção** é aberta na guia **Configuração**, onde várias opções do pipeline devem ser definidas. Essas opções são agrupadas em seções que podem ser recolhidas e são descritas nas etapas a seguir.

   1. Forneça um nome descritivo para o pipeline no campo **Nome do pipeline**.

   1. Na seção **Código fonte**, você define de onde o pipeline recuperará o código que processa.

      * **Repositório**: define de qual repositório Git o pipeline deve recuperar o código.

      >[!TIP]
      >
      >Consulte o documento [Configuração do programa](/help/getting-started/program-setup.md) para saber como adicionar e gerenciar repositórios no Cloud Manager.

      * **Ramificação Git**: no pipeline selecionado, define de qual ramificação o código deve ser recuperado.
      * **Localização do código**: define o caminho na ramificação do repositório selecionado do qual o pipeline deve recuperar o código.

      ![Definir repositórios para o pipeline](/help/assets/configure-pipelines/add-prod2.png)

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

1. Clique em **Continuar** para avançar até a guia **Teste de preparo**, onde é possível configurar o teste de desempenho do AEM Sites e do AEM Assets, dependendo das licenças de produto que você possui.

   >[!TIP]
   >
   >Consulte [Teste de qualidade do código](/help/using/code-quality-testing.md#performance-testing) para obter mais detalhes sobre as opções disponíveis na guia **Teste de preparo**.

   1. Na seção **Entrega de conteúdo de sites/Peso de carga distribuído**, configure o teste de desempenho do site com base na ponderação de solicitações de página entre três conjuntos de páginas. Você pode habilitar ou desabilitar os conjuntos de páginas conforme necessário.

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

Depois de configurar o pipeline, você implantará o código. Consulte [Implantação de código](/help/using/code-deployment.md) para obter mais detalhes.

## Tutorial em vídeo {#video-tutorial-one}

Este vídeo fornece uma visão geral do processo de criação de pipeline, que é detalhado neste documento.

>[!VIDEO](https://video.tv.adobe.com/v/327605?captions=por_br)
