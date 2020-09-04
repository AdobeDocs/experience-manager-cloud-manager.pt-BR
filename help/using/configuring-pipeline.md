---
title: Configurar o pipeline de CI/CD
seo-title: Configurar o pipeline de CI/CD
description: Siga esta página para definir as configurações de pipeline do Gerenciador de nuvem.
seo-description: 'Antes da start de implantar o código, é necessário definir as configurações de pipeline do Gerenciador da AEM Cloud. '
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
translation-type: tm+mt
source-git-commit: c35398110e9d8311bf58f217efdd082cf0cfd90a
workflow-type: tm+mt
source-wordcount: '1751'
ht-degree: 2%

---


# Configurar o pipeline de CI/CD {#configure-your-ci-cd-pipeline}

A página a seguir explica como configurar o **Pipeline**. Para consultar mais informações conceituais sobre como o pipeline funciona, consulte a visão geral [do pipeline de](ci-cd-pipeline.md)IC/CD.

## Tutorial em vídeo {#video-tutorial-one}

### Configuração do pipeline no Cloud Manager {#config-pipeline-video}

A configuração do CI/CD Production Pipeline define o acionador que iniciará o pipeline, os parâmetros que controlam a implantação da produção e os parâmetros de teste de desempenho.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)


## Como entender o fluxo {#understanding-the-flow}

Você pode configurar o pipeline no bloco **Configurações de pipeline** na interface do usuário do [!UICONTROL Cloud Manager].

O Gerenciador de implantação é responsável pela configuração do pipeline. Ao fazer isso, selecione primeiro uma ramificação do Repositório **Git**. A configuração do pipeline consiste em:

* definindo o acionador que irá start o pipeline.
* definição dos parâmetros que controlam a implantação de produção.
* configuração dos parâmetros de teste de desempenho.

## Configuração do pipeline {#setting-up-the-pipeline}

>[!CAUTION]
>
>O pipeline não pode ser configurado até que o repositório Git tenha pelo menos uma ramificação e a Configuração [do](setting-up-program.md) Programa esteja concluída.

Antes de start para implantar seu código, você deve definir as configurações de pipeline do [!UICONTROL Cloud Manager].

>[!NOTE]
>
>É possível alterar as configurações do pipeline após a configuração inicial.

### Configurar as configurações de pipeline de [!UICONTROL Cloud Manager] {#configuring-the-pipeline-settings-from-cloud-manager}

Depois de configurar seu programa usando a [!UICONTROL Cloud Manager] interface do usuário, você estará pronto para configurar seu pipeline.

Siga estas etapas para configurar o comportamento e as preferências do seu pipeline:

1. Clique em **Configurar pipeline** para configurar e configurar seu pipeline.

   ![](assets/Setup-Pipeline.png)

1. A tela **Setup Pipeline (Instalar pipeline** ) é exibida.

   O assistente de três etapas permite configurar sua **Ramificação**, **Ambientes** e ambiente **de teste** .
Selecione a ramificação Git e clique em **Avançar**.

   >[!NOTE]
   >
   >As ramificações encontradas no repositório Git estão vinculadas ao seu programa.

   ![](assets/Configure_ci-cd-2.png)


1. Acesse a guia **Ambientes** para selecionar as opções **Estágio** e **Produção** .

   Você pode definir o acionador para start do pipeline:

   * **On Git Changes** (Alterações no Git) - start o pipeline do CI/CD sempre que houver confirmações adicionadas ao ramo do git configurado. Mesmo se você selecionar essa opção, sempre poderá start o pipeline manualmente.
   * **Manual** - usar a interface de usuário para start manualmente o pipeline.

   Durante a configuração ou edição do pipeline, o Gerenciador de implantação tem a opção de definir o comportamento do pipeline quando uma falha importante for encontrada em qualquer uma das portas de qualidade, como Qualidade de código, Teste de segurança e Teste de desempenho.

   Isso é útil para clientes que desejam processos mais automatizados. As opções disponíveis são:

* **Perguntar sempre** - Essa é a configuração padrão e requer intervenção manual em qualquer falha importante.
* **Falha imediatamente** - se selecionado, o pipeline será cancelado sempre que ocorrer uma falha importante. Isso é essencialmente emular um usuário rejeitando manualmente cada falha.
* **Continuar imediatamente** - Se selecionado, o pipeline continuará automaticamente sempre que ocorrer uma falha importante. Isso é essencialmente emular um usuário que aprova manualmente cada falha.

   Agora você define os parâmetros que controlam a implantação de produção. As três opções disponíveis são as seguintes:

* **Usar aprovação** em tempo real - uma implantação deve ser aprovada manualmente por um proprietário comercial, gerente de projeto ou gerente de implantação por meio da [!UICONTROL Cloud Manager] interface do usuário.
* **Usar a Supervisão** de CSE - Um CSE é envolvido para realmente start da implantação. Durante a configuração de pipeline ou edição quando a Superintendência CSE estiver ativada, o Gerenciador de Implantação tem a opção de selecionar:

   * **Qualquer caso**: refere-se a qualquer CSE disponível
   * **Meu CSE**: refere-se a um CSE específico atribuído ao cliente ou a seu backup, se o CSE estiver fora do escritório

* **Agendado** - Essa opção permite que o usuário ative a implantação de produção agendada.

>[!NOTE]
>
>Se a opção **Programado** estiver selecionada, você poderá programar a implantação de produção para o pipeline **após** a implantação do palco (e **Usar aprovação** de GoLive, se isso tiver sido ativado) aguardar a definição de uma programação. O usuário também pode optar por executar a implantação de produção imediatamente.
>
>Consulte [**Implantar seu código**](deploying-code.md) para definir a programação de implantação ou executar a produção imediatamente.

![](assets/configure-pipeline3.png)

>[!NOTE]
>
>A opção **Usar Supervisão** de CSE não está disponível para todos os clientes.

**Aprovar após a implantação do estágio**

Há uma etapa opcional **Aprovar após a implantação** do estágio que pode ser configurada no pipeline de produção.
Isso está ativado em uma nova opção na tela Edição **de** Pipeline:

![](assets/post_deployment1.png)

Em seguida, é mostrado como uma etapa separada durante a execução do pipeline:

![](assets/post_deployment2.png)

>[!NOTE]
>
>**Aprovar após a implantação** do estágio funciona de forma semelhante à aprovação antes da implantação da produção, mas ocorre imediatamente após a etapa de implantação do estágio, ou seja, antes que qualquer teste seja feito, comparado com a aprovação antes da implantação da produção, que é feita após a conclusão de todos os testes.

**Invalidação do Dispatcher**

Como um Gerenciador de implantação, você tem a oportunidade de configurar um conjunto de caminhos de conteúdo que serão **invalidados** ou **liberados** do cache do Dispatcher AEM para instâncias de publicação, ao configurar ou editar o pipeline.

Você pode configurar um conjunto separado de caminhos para a implantação de Estágio e Produção. Se configurado, essas ações de cache serão executadas como parte da etapa do pipeline de implantação, logo após a implantação de qualquer pacote de conteúdo. Essas configurações usam o comportamento padrão AEM Dispatcher - invalidate executa uma invalidação de cache, semelhante a quando o conteúdo é ativado do autor para publicar; flush executa uma exclusão de cache.

Em geral, o uso da ação de invalidação é preferível, mas pode haver casos em que a limpeza é necessária, especialmente ao usar AEM bibliotecas clientes HTML.

>[!NOTE]
>
>Consulte Visão geral [do](dispatcher-configurations.md) Dispatcher para obter mais informações sobre o armazenamento em cache do Dispatcher.

Siga as etapas abaixo para configurar as validações do Dispatcher:

1. Clique em **Configurar** no cabeçalho Configuração do Dispatcher

   ![](assets/image2018-8-7_14-53-24.png)

1. Insira o caminho, selecione a ação do **Tipo** e clique em **Adicionar**. É possível especificar até 100 caminhos por ambiente. Depois de adicionar os caminhos, clique em **Aplicar**.

   ![](assets/image2018-8-7_14-58-11.png)

1. Quando voltar à página Configurações **do** pipeline, você verá um resumo atualizado das seleções.

   Clique em **Salvar** para persistir nesta configuração.

   ![](assets/image2018-8-7_15-4-30.png)


1. Acesse a guia **Teste** para definir seus critérios de teste para o seu programa.

   Agora, você pode configurar os parâmetros de teste de desempenho.

   Você pode configurar o Teste de desempenho *AEM Sites* e *AEM Assets* , dependendo dos produtos licenciados.

   **AEM Sites:**

   O Cloud Manager executa testes de desempenho para programas AEM Sites, solicitando páginas (como um usuário não autenticado por padrão) no servidor de publicação do palco por um período de teste de 30 minutos e medindo o tempo de resposta para cada página, bem como várias métricas no nível do sistema.

   Antes do start do período de teste de 30 minutos, o Cloud Manager rastreará o ambiente do Palco usando um conjunto de um ou mais URLs *semente* configurados pelo engenheiro de sucesso do cliente. A partir desses URLs, o HTML de cada página é inspecionado e os links são percorridos de uma maneira ampla. Esse processo de rastreamento é limitado a um máximo de 5000 páginas. As solicitações do rastreador têm um tempo limite fixo de 10 segundos.

   As páginas são selecionadas por três conjuntos **de** páginas; você pode escolher em qualquer lugar de um a todos os três conjuntos. A distribuição do tráfego baseia-se no número de conjuntos selecionados, ou seja, se todos os três forem selecionados, 33% do total de visualizações de página são colocados em cada conjunto; se dois forem selecionados, 50% serão direcionados para cada conjunto; se um estiver selecionado, 100% do tráfego vai para esse conjunto.

   Por exemplo, digamos que há uma divisão de 50%/50% entre as Páginas ativas populares e as Novas páginas definidas (neste exemplo, Outras páginas ao vivo não são usadas) e o conjunto Novas páginas contém 3000 páginas. As visualizações de página por minuto KPI é definido como 200. Durante o período de teste de 30 minutos:

   * Cada uma das 25 páginas no conjunto de Páginas ativas populares será acessada 240 vezes - ((200 * 0.5) / 25) * 30 = 120

   * Cada uma das 3000 páginas no conjunto Novas páginas será acessada uma vez - ((200 * 0.5) / 3000) * 30 = 1

   ![](assets/Configuring_Pipeline_AEM-Sites.png)

   Consulte Teste [de desempenho](#authenticated-performance-testing) autenticado para obter mais detalhes.

   **Ativos AEM:**

   O Cloud Manager executa testes de desempenho para programas AEM Assets, fazendo upload de ativos repetidamente por um período de teste de 30 minutos e medindo o tempo de processamento de cada ativo, bem como de várias métricas no nível do sistema. Esse recurso pode carregar imagens e documentos PDF. A distribuição de quantos ativos de cada tipo são carregados por minuto é definida na tela Configuração do pipeline ou Editar.

   Por exemplo, se uma divisão 70/30 for usada, como mostra a figura abaixo. Há 10 ativos carregados por minuto, 7 imagens serão carregadas por minuto e 3 documentos.

   ![](assets/Configuring_Pipeline_AEM-Assets.png)

   >[!NOTE]
   >
   >Há uma imagem padrão e um documento PDF, mas, na maioria dos casos, os clientes desejam carregar seus próprios ativos. Isso pode ser feito na tela Configuração do pipeline ou Editar. Formatos de imagem comuns, como JPEG, PNG, GIF e BMP são suportados junto com arquivos Photoshop, Illustrator e Postscript.

1. Clique em **Salvar** para concluir a configuração do processo de pipeline.

   >[!NOTE]
   >
   >Além disso, depois de configurar o pipeline, você ainda poderá editar configurações para o mesmo usando o bloco de Configurações **do pipeline de** produção da [!UICONTROL Cloud Manager] interface do usuário.

   ![](assets/Production-Pipeline.png)

### Teste de desempenho autenticado {#authenticated-performance-testing}

Os clientes do AMS com sites autenticados podem especificar um nome de usuário e uma senha que o Cloud Manager usará para acessar o site durante o Teste de desempenho do site.

O nome de usuário e a senha são especificados como Variáveis [](/help/using/build-environment-details.md#pipeline-variables) Pipeline com os nomes `CM_PERF_TEST_BASIC_USERNAME` e `CM_PERF_TEST_BASIC_PASSWORD`.

Embora não seja estritamente necessário, é recomendável usar o tipo de variável de string para o nome de usuário e o tipo de variável secretString para a senha. Se ambos forem especificados, todas as solicitações do crawler de teste de desempenho e dos usuários virtuais de teste conterão essas credenciais como autenticação HTTP Basic.

Para definir essas variáveis usando a CLI [do](https://github.com/adobe/aio-cli-plugin-cloudmanager)Cloud Manager, execute:

`$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>`

## Pipelines que não são de produção e qualidade de código

Para além do principal gasoduto que vai para a fase de construção e de produção, os clientes estão em condições de instalar gasodutos adicionais, denominados &quot;gasodutos **não produtivos&quot;**. Esses pipelines sempre executam as etapas de qualidade de compilação e código. Como opção, eles também podem implantar no ambiente Adobe Managed Services.

## Tutorial em vídeo {#video-tutorial-two}

### Pipelines de gerenciamento de nuvem somente para produção e qualidade de código {#non-prod-video}

IC/CD Os gasodutos de não-produção são divididos em duas categorias, gasodutos de qualidade do código e pipelines de implantação. A qualidade do código anula todos os códigos de uma ramificação Git para criar e ser avaliada em relação à verificação da qualidade do código do Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

Na tela inicial, esses pipelines são listados em um novo cartão:

1. Acesse o bloco Pipelines **de** não produção na tela inicial do Cloud Manager.

   ![](assets/Non-Production-Pipeline.png)

1. Clique no botão Adicionar para especificar o Nome do Pipeline, o Tipo de Pipeline e a Ramificação Git.

   Além disso, também é possível configurar o Acionador de implantação e o Comportamento de falha importante nas Opções de pipeline.

   ![](assets/non-prod-pipe.png)

1. Clique em **Salvar** e o pipeline é mostrado no cartão na tela inicial com três ações:

   * **Editar** - permite a edição das configurações de pipeline
   * **Detalhe** - exibe a última execução do pipeline (se houver um)
   * **Build** - navega até a página de execução, a partir da qual o pipeline pode ser executado

   ![](assets/Non-prod-2.png)

   >[!NOTE]
   >
   >Enquanto o pipeline estiver em execução, a etapa atual será exibida e somente a ação **Detalhes** estará disponível.

## Próximas etapas {#the-next-steps}

Depois de configurar o pipeline, é necessário implantar seu código.

Consulte [Implantar seu código](deploying-code.md) para obter mais detalhes.
