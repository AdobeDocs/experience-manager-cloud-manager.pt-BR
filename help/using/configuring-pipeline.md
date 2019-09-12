---
title: Configurar seu pipeline CI/CD
seo-title: Configurar seu pipeline CI/CD
description: Siga esta página para configurar as configurações de pipeline do Gerenciador de nuvem.
seo-description: 'Antes de começar a implantar seu código, você deve configurar suas configurações do pipeline do Gerenciador de nuvem do AEM. '
uuid: 35 fd 56 ac-dc 9 c -4 aca -8 anúncio 6-36 c 29 c 4 ec 497
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: usando
content-type: referência
discoiquuid: ba 6 c 763 a-b 78 a -439 e -8 c 40-367203 a 719 b 3
translation-type: tm+mt
source-git-commit: 862501f28f5104d0829a6d2d2ad5f5ce9f8ba341

---


# Configurar seu pipeline CI/CD {#configure-your-ci-cd-pipeline}

A página a seguir explica como configurar **o Pipeline**. Para analisar informações mais conceituais sobre como o pipeline funciona, consulte a visão geral do pipeline [CI/CD](ci-cd-pipeline.md).

## Como entender o fluxo {#understanding-the-flow}

Você pode configurar seu pipeline no bloco Configurações **do pipeline na** [!UICONTROL Cloud Manager] interface do usuário.

O Gerenciador de implantação é responsável pela configuração do pipeline. Ao fazer isso, primeiro selecione uma ramificação a partir do **Git Repository**. A configuração do pipeline consiste em:

* definindo o acionador que iniciará o pipeline.
* definindo os parâmetros que controlam a implantação de produção.
* configurar os parâmetros de teste de desempenho.

## Configuração do pipeline {#setting-up-the-pipeline}

>[!CAUTION]
>
>O pipeline não pode ser configurado até que o repositório Git tenha pelo menos um ramificação e [a Configuração](setting-up-program.md) de programa seja concluída.

Antes de começar a implantar seu código, você deve configurar as configurações do seu pipeline a partir do [!UICONTROL Cloud Manager].

>[!NOTE]
>
>É possível alterar as configurações do pipeline após a configuração inicial.

### Configuração das Configurações do pipeline de [!UICONTROL Cloud Manager]{#configuring-the-pipeline-settings-from-cloud-manager}

Depois de configurar seu programa usando [!UICONTROL Cloud Manager] a interface do usuário, você estará pronto para configurar seu pipeline.

Siga estas etapas para configurar o comportamento e as preferências do seu pipeline:

1. Clique **em Configuração pipeline** para configurar e configurar seu pipeline.

   ![](assets/Configure_ci-cd-1.png)

1. A tela **de Configuração do pipeline** é exibida.

   O assistente de três etapas permite que você configure seus **ambientes de Ramificação**, **Ambientes** e **Teste** .
Selecione sua ramificação Git e clique **em Avançar**.

   >[!NOTE]
   >
   >As ramificações encontradas no repositório Git são vinculadas ao seu programa.

   ![](assets/Configure_ci-cd-2.png)


1. Acesse **a** guia Ambientes para selecionar **opções de Palco** e **Produção** .

   É possível definir o acionador para iniciar o pipeline:

   * **Em Alterações** Git - inicia o pipeline CI/CD sempre que houver vírgulas adicionadas ao ramo de git configurado. Mesmo que você selecione essa opção, você sempre pode iniciar o pipeline manualmente.
   * **Manual** - usando a interface de usuário manualmente inicie o pipeline.
   * **Programada** - essa opção estará em breve em uma versão futura.
   Durante a configuração ou edição do pipeline, o Gerenciador de implantação tem a opção de definir o comportamento do pipeline quando uma falha importante é encontrada em qualquer um dos portfólios de qualidade, como Qualidade de código, Teste de segurança e Teste de desempenho.

   Isso é útil para clientes que desejam processos mais automatizados. As opções disponíveis são:

* **Consulte cada vez** - esta é a configuração padrão e requer intervenção manual em qualquer falha importante.
* **Falha imediatamente** - se selecionado, o pipeline será cancelado sempre que ocorrer uma falha importante. Isso é essencialmente emular um usuário que rejeita manualmente cada falha.
* **Continue imediatamente** - se selecionado, o pipeline continuará automaticamente sempre que ocorrer uma falha Importante. Isso é essencialmente emular um usuário que aprovar cada falha manualmente.

   Agora, você define os parâmetros que controlam a implantação de produção. As três opções disponíveis são as seguintes:

* **Usar aprovação em tempo real** - uma implantação deve ser aprovada manualmente por um proprietário de negócios, gerente de projeto ou gerente de implantação por meio da [!UICONTROL Cloud Manager] interface do usuário.
* **Use a CSE Monitoring** - a CSE está envolvida para iniciar a implantação. Durante a configuração do pipeline ou edição quando a Supervisão CSE está ativada, o Gerenciador de implantação tem a opção de selecionar:

   * **Qualquer CSE**: refere-se a qualquer CSE disponível
   * **My CSE**: refere-se a uma CSE específica atribuída ao cliente ou ao backup, se o CSE estiver fora do escritório

* **Agendada** - Essa opção permite que o usuário ative a implantação programada de produção.

>[!NOTE]
>
>Se **a** opção Programado estiver selecionada, você poderá programar a implantação de produção para o pipeline **depois** da implantação do palco (e **Usar aprovação do golive**, se isso tiver sido ativado) para esperar que um agendamento seja definido. O usuário também pode escolher executar a implantação de produção imediatamente.
>
>Consulte [**Implantar seu código**](deploying-code.md)para definir o agendamento de implantação ou executar a produção imediatamente.

![](assets/Configure_ci-cd-3.png)

>[!NOTE]
>
>A opção **Usar supervisão** CSE não está disponível para todos os clientes.

**Dispatcher Invalidation**

Como um Gerente de implantação, você tem a oportunidade de configurar um conjunto de caminhos que serão **invalidados** ou **liberados** do cache do AEM Dispatcher ao configurar ou editar pipeline.

Você pode configurar um conjunto separado de caminhos para implantação de Stage e Production. Se configurado, essas ações de cache serão executadas como parte da etapa do pipeline de implantação, logo após a implantação de qualquer pacote de conteúdo. Essas configurações usam comportamento padrão do AEM Dispatcher - invalidate executa uma invalidação de cache, semelhante ao momento em que o conteúdo é ativado do autor para publicar; o flush realiza uma exclusão de cache.

Em geral, o uso da ação invalidate é preferível, mas pode haver casos em que a limpeza é necessária, especialmente ao usar Bibliotecas de cliente HTML do AEM.

>[!NOTE]
>
>Consulte a Visão geral [do Dispatcher](dispatcher-configurations.md) obter mais informações sobre armazenamento em cache do Dispatcher.

Siga as etapas abaixo para configurar o Dispatcher Invalidations:

1. Clique **em Configurar** abaixo do cabeçalho Configuração do Dispatcher

   ![](assets/image2018-8-7_14-53-24.png)

1. Digite o caminho, selecione a ação de **Tipo** e clique **em Adicionar**. Você pode especificar até 100 caminhos por ambiente. Após adicionar os caminhos, clique **em Aplicar**.

   ![](assets/image2018-8-7_14-58-11.png)

1. Após voltar na página **Configurações** do pipeline, você verá um resumo atualizado das seleções.

   Clique **em Salvar** para continuar a configuração.

   ![](assets/image2018-8-7_15-4-30.png)

1. Acesse a **guia Teste** para definir seus critérios de teste para o programa.

   Agora, você pode configurar os parâmetros de teste de desempenho.

   Você pode configurar *o AEM Sites* e *o Teste* de desempenho do AEM Assets, dependendo dos produtos licenciados.

   **AEM Sites:**

   O Cloud Manager executa testes de desempenho para os programas AEM Sites solicitando páginas (como um usuário não autenticado) no servidor de publicação do palco para um período de teste de 30 minutos e medir o tempo de resposta para cada página, bem como diversas métricas do sistema. As páginas são selecionadas por três conjuntos **de páginas**; você pode escolher em qualquer lugar de um a três conjuntos. A distribuição do tráfego é baseada no número de conjuntos selecionados, ou seja, se todos os três estiverem selecionados, 33% do total de exibições de página serão colocados em cada conjunto; se duas estiverem selecionadas, 50% vai para cada conjunto; se uma estiver selecionada, 100% do tráfego vai para esse conjunto.

   Por exemplo, digamos que haja uma divisão de 50%/50% entre as páginas populares populares e novas páginas (neste exemplo, Outras páginas ativas não são usadas) e o conjunto Novas páginas contém 3000 páginas. As exibições de página por minuto KPI estão definidas como 200. Durante o período de teste de 30 minutos:

   * Cada uma das 25 páginas no conjunto de Páginas ativas populares será atingida por 240 vezes - ((200 * 0.5)/ 25) * 30 = 120

   * Cada uma das 3000 páginas no conjunto Novas páginas serão acessadas uma vez - (((200 * 0.5)/ maio de) 000) * 30 = 1
   ![](assets/Configuring_Pipeline_AEM-Sites.png)

   **AEM Assets:**

   O Cloud Manager executa testes de desempenho para os programas AEM Assets fazendo upload de ativos repetidamente por um período de teste de 30 minutos e medição do tempo de processamento para cada ativo, bem como diversas métricas do sistema. Esse recurso pode carregar imagens e documentos PDF. A distribuição de quantos ativos de cada tipo são carregados por minuto é definida na tela Configuração do pipeline ou Editar.

   Por exemplo, se uma divisão 70/30 for usada, conforme visto na figura abaixo. Há 10 ativos carregados por minuto, imagens serão carregadas por minuto e 3 documentos.

   ![](assets/Configuring_Pipeline_AEM-Assets.png)

   >[!NOTE]
   >
   >Há uma imagem padrão e um documento PDF, mas, na maioria dos casos, os clientes desejam carregar seus próprios ativos. Isso pode ser feito na tela de Configuração do pipeline ou Editar. Formatos comuns de imagem como JPEG, PNG, GIF e BMP são suportados juntamente com arquivos Photoshop, Illustrator e Postscript.

1. Clique **em Salvar** para concluir a configuração do processo de pipeline.

   >[!NOTE]
   >
   >Além disso, após configurar o pipeline, ainda é possível editar as configurações da mesma forma usando o bloco de **Configurações do Pipeline de produção** na [!UICONTROL Cloud Manager] interface do usuário.

   ![](assets/Prod-Pipeline-Settings-Dialog.png)

## Apenas pipeline de não produção e código

Além do pipeline principal que implanta o palco e a produção, os clientes podem configurar gasodutos adicionais, chamados de Pipeline **de não produção**. Esses gasodutos sempre executam as etapas de compilação e qualidade do código. Opcionalmente, também podem implantar no ambiente Adobe Managed Services.

Na tela inicial, esses pipeline estão listados em um novo cartão:

1. Acesse o bloco **de Pipeline de** não produção na tela inicial do Gerenciador de nuvem.

   ![](assets/Configuring_Pipeline_Add-Production.png)

1. Clique no botão Adicionar para especificar o Nome do pipeline, o Tipo de pipeline e o Git Branch.

   Além disso, também é possível configurar o Acionador de implantação e o Comportamento importante de falha das Opções de pipeline.

   ![](assets/Configuring_Pipeline_Add-Production2.png)

1. Clique **em Salvar** e o pipeline será mostrado no cartão na tela inicial com três ações:

   * **Editar** - permite a edição das configurações do pipeline
   * **Detalhe** - exibe a execução do último pipeline (se houver um)
   * **Construir** - navegar até a página de execução, a partir da qual o pipeline pode ser executado
   ![](assets/Configuring_Pipeline_Add-Production3.png)

   >[!NOTE]
   >
   >Enquanto o pipeline está em execução, a etapa atual é exibida e somente a **ação Detalhes** está disponível.

## Próximas etapas {#the-next-steps}

Depois de configurar o pipeline, você precisa implantar seu código.

Consulte [Implantar seu código](deploying-code.md) para obter mais detalhes.
