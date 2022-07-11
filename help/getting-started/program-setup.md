---
title: Configuração do programa
description: Após a integração, o proprietário da empresa precisará fazer uma configuração inicial do programa.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 1%

---


# Configuração do programa {#program-setup}

Após a integração, o proprietário da empresa conclui a configuração inicial do programa, incluindo a definição da descrição do programa e a definição dos indicadores-chave de desempenho (KPIs), que são usados para testes de desempenho.

## Configuração do programa com [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Siga estas etapas para configurar o programa e definir KPIs.

1. Faça logon no Cloud Manager em [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e selecione a organização apropriada.

1. Clique em **Programa de configuração** para iniciar o processo de configuração.

   ![Configurar programa](/help/assets/set-up-program/setup1.png)

1. No **Programa de configuração** você pode inserir informações do programa em três guias:

   * **Geral**
   * **KPI**
   * **Provisionamento**

1. No **Geral** , adicione uma descrição para o programa e, como opção, carregue uma miniatura clicando em **Alterar foto**.

   ![Guia General](/help/assets/Setup_Program-General.png)

1. No **KPI** , defina seus KPIs. Neste exemplo, KPIs separados são definidos para **AEM Sites** e **AEM Assets**. Você poderá especificar os KPIs para os produtos que licenciou.

   * Consulte a seção [KPIs](#kpis) para obter mais detalhes sobre como os KPIs são medidos no Cloud Manager.

   ![Definição de KPIs](/help/assets/Setup_Program-KPIs.png)

1. No **Provisionamento** , você pode definir as opções de dimensionamento sob demanda para seus ambientes, se o dimensionamento automático estiver ativado para o seu programa.

   * O dimensionamento automático se aplica somente ao ambiente de produção e pode não estar disponível para todos os programas do cliente.

   ![Opções de provisionamento](/help/assets/Setup_Program-Provisioning.png)

1. Clique em **Salvar** para concluir o assistente de configuração.

Seu programa será criado. Pode levar vários minutos para que os recursos sejam provisionados antes que o programa esteja pronto para uso.

## Editar um programa {#editing-program}

É possível editar programas depois que eles forem configurados. Siga estas etapas para editar um programa.

1. Faça logon no Cloud Manager em [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e selecione a organização apropriada.

1. Navegue até o programa na tela inicial do Cloud Manager.

1. Clique em **Editar programa** para atualizar ou modificar seu programa do **Visão geral** página.

   ![Opção Editar programa](/help/assets/set-up-program/edit-program1.png)

1. O **Editar programa** será exibida, permitindo atualizar seu programa. Consulte a seção [Configuração do programa com o Cloud Manager](#program-setup-cloud-manager) para obter detalhes sobre os campos disponíveis.

   ![Caixa de diálogo Editar programa](/help/assets/set-up-program/edit-program-general.png)

1. Clique em **Atualizar** para salvar as alterações.

Observe que as alterações são salvas imediatamente no Cloud Manager, mas não serão refletidas em seus ambientes até a próxima execução do pipeline.

Se você ainda não criou um pipeline, consulte os documentos [Configuração de pipeline de produção](/help/using/production-pipelines.md) e [Configuração de pipeline de não produção.](/help/using/non-production-pipelines.md)

## Alternância entre programas {#swithing-programs}

Ao trabalhar em um programa, você pode mudar rapidamente para outro programa sem voltar à página de visão geral do Cloud Manager.

Use a barra de ações para alternar para outro programa, editar o programa atual ou adicionar um novo programa.

![Seletor de programa](/help/assets/set-up-program/setup2.png)

## KPIs {#kpis}

Os KPIs de sites são medidos em testes executados no ambiente de preparo. Normalmente, esses KPIs são dimensionados para baixo para se ajustarem aos recursos do ambiente de preparo.

Por exemplo, um usuário que espera uma média de 1000 exibições de página por minuto em seu ambiente de produção e tem quatro servidores de dispatcher/publicação em produção deve dimensionar isso para 250 exibições de página por minuto. Isso pressupõe que seu ambiente de preparo consiste em apenas um único par de servidores de dispatcher/publicação.

O teste de desempenho do ativo é feito fazendo o upload de ativos repetidamente durante um período de teste de 30 minutos e medindo o tempo de processamento de cada ativo, bem como de várias métricas no nível do sistema.

Você pode ter uma rede de entrega de conteúdo (CDN), como Akamai ou CloudFront em frente ao ambiente de produção. Since [!UICONTROL Cloud Manager] Testa diretamente o ambiente de preparo, o KPI deve refletir somente o tráfego que deve passar pela CDN, ou seja, o cache não é utilizado. Normalmente, esse será um subconjunto relativamente pequeno do tráfego total de produção.

## Visão geral do vídeo {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
