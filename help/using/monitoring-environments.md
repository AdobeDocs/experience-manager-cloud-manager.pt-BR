---
title: Monitorar ambientes
description: Saiba como monitorar seus ambientes no Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 5907ca6337d33c26ff19a14bfeb358cd9f7b935d
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---


# Monitorar ambientes {#monitoring-environments}

Saiba como monitorar seus ambientes no Cloud Manager.

## Limites de métrica {#thresholds}

Monitoramento do sistema em [!UICONTROL Cloud Manager] é feito observando as instâncias individuais em um ambiente e rastreando diversas métricas para cada instância. Cada métrica tem dois limites definidos: um limite de aviso e um limite crítico.

Se uma métrica ultrapassar seu limite crítico, ela será considerada como estando em estado crítico. Se uma métrica estiver acima do limite de aviso (mas abaixo de seu limite crítico), ela será considerada um estado de aviso. Os limites são definidos pelo Adobe Managed Services e podem ser visualizados em [!UICONTROL Cloud Manager]. Na maioria dos casos, os limites são consistentes entre os clientes, mas há casos em que o Adobe Managed Services modificará os limites para atender às necessidades específicas do cliente. As dúvidas sobre os limites devem ser direcionadas ao seu Engenheiro de Sucesso do Cliente (CSE).

## Acesso ao monitoramento do sistema {#accessing-system-monitoring}

Siga estas etapas para acessar o Monitoramento do sistema.

1. Faça logon em **Managed Services - Programas** página de aterrissagem.

   ![Programas de serviços gerenciados](/help/assets/ProgramLanding.png)

1. Clique no quarto ícone no cartão do programa.

   ![Configurações](/help/assets/first-timea1.png)


Como alternativa, você pode navegar até a **Monitoramento de sistema** página de aterrissagem por meio do **Relatórios** item de menu de navegação global em [!UICONTROL Cloud Manager].

## Visão geral do monitoramento do sistema {#system-monitoring-overview}

A página de visão geral de Monitoramento do Sistema lista os ambientes monitorados no programa e relata sobre sua integridade de alto nível em quatro categorias separadas:

* Host
* Armazenamento
* Rede
* Aplicativo

O status em cada categoria é um resumo de métricas individuais. Se qualquer métrica em uma categoria estiver no estado crítico, a categoria inteira estará em um estado crítico para a finalidade da página de visão geral. O mesmo resumo pode ser visualizado em um nível de ambiente e em um nível de instância.

![Visão geral do monitoramento do sistema](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Por padrão, ao navegar para essa página, as instâncias do ambiente de produção são visíveis, mas outros ambientes também podem ser visualizados.

## Detalhes do monitoramento do sistema {#system-monitoring-detail}

Para exibir os detalhes de métricas específicas, você pode clicar em uma das categorias na navegação à esquerda ou clicar em um dos indicadores de categoria para uma instância específica. Cada página de detalhes mostra uma série de gráficos para as métricas dentro dessa categoria. Você pode exibir as métricas de todas as instâncias em um ambiente ou para uma instância específica. Você pode alternar entre o ambiente e as instâncias usando as caixas suspensas no canto superior direito.

![Selecionar ambiente](/help/assets/System_Monitoring1.png)

A navegação à esquerda mostrará as métricas disponíveis na categoria selecionada no momento, para as quais há dados para o ambiente e as instâncias selecionadas no momento.

![Métricas de monitoramento](/help/assets/System_Monitoring2.png)

Um gráfico individual mostrará o status e um gráfico dos dados ao longo do tempo, juntamente com os limites. Se várias instâncias forem exibidas, os dados de cada instância serão em uma série separada.

![Gráfico de métricas](/help/assets/Monitoring_Graphs1.png)

As séries individuais podem ser ocultadas em um gráfico clicando nas séries na legenda.
Por exemplo, se você clicar na série de limites de aviso, verá apenas o limite crítico.

![Modificar gráfico](/help/assets/Monitoring_Graphs2.png)

### Definições de Métricas {#metric-definitions}

#### Host {#host}

* **Carregar por núcleo**: O número de processos que estão sendo executados pela CPU ou que estão em um estado de espera em média por um período de um (carga1), cinco (carga5) e quinze (carga15) minutos
* **Contagem de Processos**: O número de processos atualmente abertos
* **Contagem de usuários**: O número de usuários com uma sessão de shell ativa
* **Uso de memória**: A porcentagem da memória do sistema alocada no momento
* **Memória JVM**: O tamanho (em megabytes) do heap Java alocado
* **Espaço de Geração Antiga**: A porcentagem de memória de geração antiga da JVM atualmente alocada

#### Rede {#network}

* **Verificação de porta CQ**: O tempo de resposta em segundos para acessar a porta do AEM ou Dispatcher
   * Há métricas diferentes para autor, publicação e dispatcher.

#### Armazenamento {#storage}

* **Espaço em disco**: O espaço em disco usado (em megabytes) para cada ponto de montagem no host
   * Há métricas diferentes para cada ponto de montagem.
   * No mínimo, há métricas para `/` e `/mnt`, mas podem estar disponíveis métricas adicionais de ponto de montagem, dependendo da configuração específica da instância.
* **Tamanho da pasta**
* **Loja de segmentos AEM**: O espaço em disco usado (em gigabytes) para a Loja de segmentos de AEM

#### Aplicativo {#application}

* **Agente de replicação**: O tempo (em segundos) para um evento de replicação de teste
   * Há métricas separadas para cada agente de replicação.
* **Liberação do Dispatcher**: O número de itens atualmente na fila de liberação do dispatcher

## Relatórios de SLA {#sla-reporting}

Os clientes podem ver o desempenho de seu ambiente de produção AEM em relação ao contrato de nível de serviço (SLA). Isso está disponível por meio de um submenu no **Relatórios** tela.

O gráfico a seguir mostra o nível mensal de SLA para 2018.

![Gráfico SLA 2018](/help/assets/SLA-Reports-one.png)

Assim como nos gráficos de monitoramento do sistema, o acumulado em um ponto de dados mostra os valores específicos daquele mês.

![Substituição do ponto de dados](/help/assets/SLA-Reports-two.png)

O **Análise de evento** A seção deste gráfico mostra o conjunto de incidentes que ocorreram para o programa durante o ano atualmente selecionado. Cada incidente tem um intervalo de tempo, uma causa e um conjunto de comentários.

![Análise de evento](/help/assets/sla-reporting3.png)

## Métricas de SLA {#sla-metrics}

* **Contrato de Autor**: Este é o SLA definido em seu contrato com o Adobe Managed Services para o nível de criação.
* **SLA de autor do AMS**: Esse é o tempo de atividade medido dos incidentes de fatoração do nível do autor de produção causados pelo Adobe ou por nossos fornecedores.
* **SLA do autor**: Esse é o tempo de atividade medido do nível de criação ignorando o tempo de inatividade programado, como janelas de manutenção.
* **Contrato de usuário final**: Este é o SLA definido em seu contrato com o Adobe Managed Services para o nível de publicação.
* **SLA de Usuário Final do AMS**: Esse é o tempo de atividade medido dos incidentes de fatoração do nível de publicação de produção causados pelo Adobe ou por nossos fornecedores.
* **SLA de usuário final**: Esse é o tempo de atividade medido do nível de publicação ignorando o tempo de inatividade programado, como janelas de manutenção.

## Tutorial em vídeo {#video-tutorial}

Este vídeo fornece uma visão geral do uso dos gráficos produzidos pelos Relatórios do Cloud Manager para uma visualização nos ambientes do programa.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
