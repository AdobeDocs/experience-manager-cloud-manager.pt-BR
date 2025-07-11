---
title: Configuração do programa
description: Após a integração, o proprietário da empresa precisa fazer uma configuração inicial do programa.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 93%

---


# Configuração do programa {#program-setup}

Após a integração, o proprietário da empresa configura o programa adicionando uma descrição e definindo indicadores principais de desempenho (KPIs). Esses KPIs são usados para testes de desempenho.

## Configuração do programa com o [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Siga estas etapas para configurar o programa e definir KPIs.

1. Faça logon no Cloud Manager, em [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com), e selecione a organização apropriada.

1. Clique em **Configurar programa** para iniciar o processo de configuração.

   ![Configurar programa](/help/assets/set-up-program/setup1.png)

1. Na caixa de diálogo **Configurar programa**, você pode inserir informações do programa em três guias:

   * **Geral**
   * **KPI**
   * **Provisionamento**

1. Na guia **Geral**, adicione uma descrição para o programa e, como opção, faça upload de uma miniatura clicando em **Alterar foto**.

   ![Guia Geral](/help/assets/Setup_Program-General.png)

1. Na guia **KPI**, defina seus KPIs. Neste exemplo, KPIs separados são definidos para o **AEM Sites** e para o **AEM Assets**. Especifique os KPIs dos produtos que você licenciou.

   Consulte a seção [KPIs](#kpis) para obter mais detalhes sobre como os KPIs são medidos no Cloud Manager.

   ![Definição de KPIs](/help/assets/Setup_Program-KPIs.png)

1. Na guia **Provisionamento**, é possível definir as opções de Dimensionamento sob demanda para seus ambientes, se o dimensionamento automático estiver habilitado para o seu programa.

   O dimensionamento automático se aplica somente ao ambiente de produção e pode não estar disponível para todos os programas de clientes.

   ![Opções de provisionamento](/help/assets/Setup_Program-Provisioning.png)

1. Clique em **Salvar**.

Seu programa foi criado. Pode levar vários minutos para que os recursos sejam provisionados antes que o programa esteja pronto para uso.

## Editar um programa {#editing-program}

É possível editar programas depois que eles forem configurados. Siga estas etapas para editar um programa.

1. Faça logon no Cloud Manager, em [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com), e selecione a organização apropriada.

1. Navegue até o programa na tela inicial do Cloud Manager.

1. Clique em **Editar programa** para atualizar ou modificar o seu programa a partir da página **Visão geral**.

   ![Opção Editar programa](/help/assets/set-up-program/edit-program1.png)

1. A caixa de diálogo **Editar programa** será exibida, permitindo atualizar seu programa. Consulte a seção [Configuração do programa com o Cloud Manager](#program-setup-cloud-manager) para obter detalhes sobre os campos disponíveis.

   ![Caixa de diálogo Editar programa](/help/assets/set-up-program/edit-program-general.png)

1. Clique em **Atualizar** para salvar as alterações.

As alterações são salvas imediatamente no Cloud Manager, mas só serão refletidas em seus ambientes na próxima execução do pipeline.

Se você ainda não tiver criado um pipeline, consulte os documentos [Configuração de pipelines de produção](/help/using/production-pipelines.md) e [Configuração de pipelines de não produção](/help/using/non-production-pipelines.md).

## Alternar entre programas {#swithing-programs}

Ao trabalhar em um programa, é possível mudar rapidamente para outro programa sem voltar à página de visão geral do Cloud Manager.

Use a barra de ações para alternar para outro programa, editar o programa atual ou adicionar um novo programa.

![Seletor de programas](/help/assets/set-up-program/setup2.png)

## KPIs {#kpis}

Os KPIs de sites são medidos em testes executados no ambiente de preparo. Normalmente, esses KPIs são dimensionados para baixo para se ajustarem aos recursos do ambiente de preparo.

Por exemplo, um usuário que espera uma média de 1000 visualizações de página por minuto em seu ambiente de produção e tem quatro servidores de Dispatcher/publicação em produção deve dimensionar isso para 250 exibições de página por minuto. Esse cenário pressupõe que o ambiente de preparo consiste em apenas um único par de servidores do Dispatcher/Publish.

O teste de desempenho do Assets envolve uploads repetidos de ativos em um período de 30 minutos. O tempo de processamento de cada ativo e várias métricas no nível do sistema são medidos durante o teste. 

Você pode ter uma rede de entrega de conteúdo (CDN), como Akamai ou CloudFront, em frente ao ambiente de produção. Como o [!UICONTROL Cloud Manager] testa diretamente no ambiente de preparo, o KPI deve refletir somente o tráfego que deve passar pela CDN. Ou seja, o cache não é utilizado. Normalmente, essa experiência é um subconjunto relativamente pequeno do tráfego total de produção.

## Vídeo de visão geral {#video}

>[!VIDEO](https://video.tv.adobe.com/v/34268?captions=por_br)
