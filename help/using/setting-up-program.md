---
title: Configure seu programa
seo-title: Configure seu programa
description: Após o embarque, o proprietário da empresa precisará fazer uma configuração inicial do programa.
seo-description: 'Após a integração, o proprietário da empresa precisará fazer uma configuração inicial do Adobe AEM Cloud Manager. Isso envolve definir a descrição do programa e definir os KPIs que serão usados para testes de desempenho. '
uuid: 9ecf8743-1f5a-4744-86af-e2256567642f
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introdução
discoiquuid: c2393540-e852-4f7c-aafd-1427209065d2
translation-type: tm+mt
source-git-commit: 2c05eb4610e35d5126c6c67e44f4b71f3026c887

---


# Configure seu programa {#setup-your-program}

Após a integração, o proprietário da empresa precisará concluir alguma configuração inicial do programa. Isso envolve definir a descrição do programa e os Indicadores-chave de desempenho (KPIs) que serão usados para testes de desempenho. Como opção, uma miniatura pode ser carregada. Além disso, o proprietário da empresa pode configurar o provisionamento de ambientes ao configurar o programa.

Os KPIs definidos servem como uma linha de base para o teste de desempenho, que é passado cada vez que o pipeline é executado.

>[!NOTE]
>
>Os KPIs definidos são medidos em testes executados no ambiente do **palco** . Normalmente, esses KPIs são reduzidos para se ajustarem aos recursos do ambiente do palco.
>
>Por exemplo, um usuário que espera uma média de 1.000 exibições de página por minuto em seu **Ambiente** de produção e que tenha quatro servidores de despacho/publicação em produção deve dimensionar isso para 250 exibições de página por minuto (considerando que seu ambiente de estágio consiste em apenas um par de despachante/servidor de publicação).
>
>Além disso, muitos usuários terão uma Rede de entrega de conteúdo (CDN), como Akamai ou CloudFront em frente ao ambiente de produção. Como [!UICONTROL Cloud Manager] os testes contra o ambiente do palco são feitos diretamente, o KPI deve refletir apenas o tráfego que se espera que passe pelo CDN, ou seja, o cache não tem acesso. Normalmente, esse será um subconjunto relativamente pequeno do tráfego total de produção.

## Usar [!UICONTROL Cloud Manager] para configurar seu programa {#using-cloud-manager-to-setup-your-program}

Siga as etapas abaixo para configurar o programa e definir KPIs:

1. Clique em **Programa** de instalação para iniciar o processo de configuração em [!UICONTROL Cloud Manager].

   ![](assets/SetUpProgram1.png)

1. A tela **Setup Program** (Programa de configuração) exibe Edit Program Information (Editar informações do programa).

1. Você verá três opções como **Geral**, **KPI** e guia **Provisionamento** .

1. Na guia **Geral** , carregue uma miniatura em seu programa. Você também pode adicionar uma descrição relevante ao seu programa.

   ![](assets/Setup_Program-General.png)

1. Em **KPI**, você pode definir seus dois KPIs (expectativas para cada implantação). KPIs separados são definidos para **AEM Sites** e **AEM Assets**. Você poderá especificar os KPIs para os produtos licenciados.

   **AEM Sites**

   1. Qual é o tempo de resposta do 95º percentil que é aceitável para você?

      * Valor recomendado - 3 segundos
   1. Quantas Exibições de página por minuto sob o pico de carga?

      * Valor recomendado - 200 visualizações de página por minuto
   **AEM Assets**

   Desde sua versão inicial, o Cloud Manager tem sido capaz de executar testes de desempenho para programas do AEM Sites. Com esta versão, o recurso foi adicionado para executar testes de desempenho para os programas do AEM Assets também. O teste de desempenho do ativo é feito fazendo upload de ativos repetidamente durante um período de teste de 30 minutos e medindo o tempo de processamento de cada ativo, bem como de várias métricas no nível do sistema.
Durante a configuração do programa, os KPIs específicos dos ativos são especificados:

   * 95% do tempo de processamento
   * Ativos carregados por minuto
   ![](assets/Setup_Program-KPIs.png)

1. Em **Provisionamento**, você pode exibir ou editar a configuração de provisionamento para ambientes de produção e não-produção em seu programa. Você verá que a **Autoescala está ativada**, se a autoescala tiver sido ativada para o programa.

   >[!NOTE]
   >
   >* O recurso de dimensionamento automático se aplica somente ao ambiente de produção e pode não estar disponível para todos os programas do cliente.
   >* A escala sob demanda não está disponível para esta versão do [!UICONTROL Cloud Manager].


   ![](assets/Setup_Program-Provisioning.png)

1. Clique em **Salvar** para concluir o assistente de configuração.

   >[!NOTE]
   >
   >Você sempre pode editar o programa depois que o programa inicial já tiver sido configurado. Siga as etapas abaixo para obter mais detalhes.

## Edição de um programa

1. Navegue até a solução na tela inicial do **Cloud Manager** .

   ![](assets/SetUpProgram5.png)

1. Selecione a solução e clique em **Editar** para atualizar ou modificar seu programa, como mostrado na figura abaixo.

   ![](assets/SetUpProgram6.png)

1. A tela **Editar programa** é exibida e permite que você atualize ou modifique seu programa.

   ![](assets/Editing_Program-screen3.png)

## Próximas etapas {#the-next-steps}

Se você já tiver configurado o **Pipeline**, a execução seguinte levará em conta as configurações atualizadas. Se você ainda não tiver configurado o pipeline, siga as etapas para configurar seu pipeline primeiro.

Consulte [Configurar o pipeline de CI/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html) para configurar o pipeline.
