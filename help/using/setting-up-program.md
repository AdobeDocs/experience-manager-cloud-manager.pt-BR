---
title: Configurar o programa
seo-title: Configurar o programa
description: Após a integração, o proprietário da empresa precisará fazer uma configuração inicial do programa.
seo-description: 'Após a integração, o proprietário da empresa precisará fazer uma configuração inicial do Adobe AEM Cloud Manager. Isso envolve definir a descrição do programa e os KPIs que serão usados para testes de desempenho. '
uuid: 9ecf8743-1f5a-4744-86af-e2256567642f
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: c2393540-e852-4f7c-aafd-1427209065d2
feature: Getting Started
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 2%

---


# Configurar o programa {#setup-your-program}

Após a integração, o proprietário da empresa precisará concluir uma configuração inicial do programa. Isso envolve definir a descrição do programa e os Indicadores-chave de desempenho (KPIs) que serão usados para testes de desempenho. Outra opção é fazer upload de uma miniatura. Além disso, o proprietário da empresa pode configurar o provisionamento de ambientes ao configurar o programa.

Os KPIs definidos servem como uma linha de base para o teste de desempenho, que é transmitido cada vez que o pipeline é executado.

>[!NOTE]
>
>Os KPIs definidos são medidos em testes executados no ambiente **stage**. Normalmente, esses KPIs são reduzidos para se adequarem aos recursos do ambiente de preparo.
>
>Por exemplo, um usuário que espera uma média de 1000 exibições de página por minuto em sua produção **Environment** e ter quatro servidores de dispatcher/publicação em produção deve dimensionar isso para 250 exibições de página por minuto (supondo que seu ambiente de estágio consista em apenas um único par de dispatcher/servidor de publicação).
>
>Além disso, muitos usuários terão uma Rede de entrega de conteúdo (CDN), como Akamai ou CloudFront em frente ao ambiente de produção. Como [!UICONTROL Cloud Manager] testa diretamente o ambiente de preparo, o KPI deve refletir somente o tráfego esperado para passar pelo CDN, ou seja, o cache está faltando. Normalmente, esse será um subconjunto relativamente pequeno do tráfego total de produção.

## Usando [!UICONTROL Cloud Manager] para configurar o programa {#using-cloud-manager-to-setup-your-program}

Siga as etapas abaixo para configurar o programa e definir KPIs:

1. Clique em **Programa de Configuração** para iniciar o processo de configuração em [!UICONTROL Cloud Manager].

   ![image1](assets/set-up-program/setup1.png)

   >[!NOTE]
   > Você sempre pode alternar, editar ou adicionar um novo programa na barra de ações, como mostrado na figura abaixo.

   ![image1](assets/set-up-program/setup2.png)


1. A tela **Programa de instalação** exibe as Informações de Editar programa.

1. Você verá três opções como **Geral**, **KPI** e **Provisionamento**.

1. Na guia **General**, carregue uma miniatura no programa. Você também pode adicionar uma descrição relevante ao seu programa.

   ![](assets/Setup_Program-General.png)

1. Em **KPI**, você pode definir seus dois KPIs (expectativas para cada implantação). KPIs separados são definidos para **AEM Sites** e **AEM Assets**. Você poderá especificar os KPIs para os produtos que licenciou.

   **AEM Sites**

   1. Qual é o tempo de resposta do 95º percentil que é aceitável para você?

      * Valor recomendado - 3 segundos
   1. Quantas Exibições de página por minuto sob o pico de carga?

      * Valor recomendado - 200 visualizações de página por minuto

   **AEM Assets**

   Desde a versão inicial, o Cloud Manager tem sido capaz de executar testes de desempenho para programas AEM Sites. Com esta versão, o recurso foi adicionado para executar testes de desempenho para programas AEM Assets também. O teste de desempenho do ativo é feito fazendo o upload de ativos repetidamente durante um período de teste de 30 minutos e medindo o tempo de processamento de cada ativo, bem como de várias métricas no nível do sistema.
Durante a configuração do programa, os KPIs específicos dos ativos são especificados:

   * 95º tempo de processamento do percentual
   * Ativos carregados por minuto

   ![](assets/Setup_Program-KPIs.png)

1. Em **Provisionamento**, você pode visualizar ou editar a configuração de provisionamento para ambientes de produção e não relacionados à produção em seu programa. Você verá **Autoscale está em**, se o autodimensionamento tiver sido ativado para o programa.

   >[!NOTE]
   >
   >* O recurso de dimensionamento automático se aplica somente ao ambiente de produção e pode não estar disponível para todos os programas do cliente.
   >* O dimensionamento sob demanda não está disponível para esta versão de [!UICONTROL Cloud Manager].


   ![](assets/Setup_Program-Provisioning.png)

1. Clique em **Save** para concluir o assistente de configuração.

   >[!NOTE]
   >
   >Você sempre poderá editar o programa depois que o programa inicial já tiver sido configurado. Siga as etapas abaixo para obter mais detalhes.

## Editar um programa

1. Navegue até a solução na tela inicial do **Cloud Manager**.

   ![](assets/SetUpProgram5.png)

1. Selecione a solução e clique em **Edit** para atualizar ou modificar o programa, conforme mostrado na figura abaixo.

   ![](assets/SetUpProgram6.png)

1. A tela **Editar Programa** é exibida e permite que você atualize ou modifique seu programa.

   ![](assets/Editing_Program-screen3.png)

## Próximas etapas {#the-next-steps}

Se você já tiver configurado o **Pipeline**, a próxima execução levará em conta as configurações atualizadas. Se ainda não tiver configurado o pipeline, siga as etapas para configurar seu pipeline primeiro.

Consulte [Configurar o pipeline de CI/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html) para configurar o pipeline.
