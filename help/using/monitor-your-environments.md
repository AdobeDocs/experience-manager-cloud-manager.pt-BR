---
title: Monitorar os ambientes
seo-title: Monitorar os ambientes
description: Saiba como monitorar seus ambientes no Cloud Manager
seo-description: Siga esta página para saber mais sobre o Monitoramento de sistema no Cloud Manager, que é feito observando as instâncias individuais em um ambiente e rastreando diversas métricas para cada instância.
feature: Environments
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '967'
ht-degree: 1%

---


# Monitoramento do sistema {#system-monitoring}

O monitoramento do sistema em [!UICONTROL Cloud Manager] é feito observando as instâncias individuais em um ambiente e rastreando diversas métricas para cada instância. Cada métrica tem dois limites definidos - um *limite de aviso* e um *limite crítico*.

Se uma métrica ultrapassar o seu limite crítico, será considerada como estando em estado crítico; se uma métrica estiver acima do limite de aviso (mas abaixo do limite crítico), ela será considerada um estado de aviso. Os limites são definidos pelo Adobe Managed Services e podem ser visualizados em [!UICONTROL Cloud Manager]. Na maioria dos casos, os limites são consistentes entre os clientes, mas há casos em que o Adobe Managed Services modificará os limites para atender às necessidades específicas do cliente. As dúvidas sobre os limites devem ser direcionadas ao seu Engenheiro de Sucesso do Cliente (CSE).

## Navegar até o Monitoramento de Sistema {#navigating-system-monitoring}

Navegar até o recurso de Monitoramento de sistema pode ser feito de duas maneiras.

1. Faça logon na landing page **Managed Services - Programas**.

   ![](assets/ProgramLanding.png)

1. Clique no quarto ícone no cartão do programa.

   ![](assets/first-timea1.png)

   *Ou*,

* Navegue até a página inicial **Monitoramento do Sistema** através do item de menu de navegação global **Relatórios** em [!UICONTROL Cloud Manager].


## Página Visão geral do monitoramento do sistema {#system-monitoring-overview-page}

A página Visão geral do monitoramento do sistema lista os ambientes monitorados no programa e relata sobre sua integridade de alto nível em quatro categorias separadas:

* **Host**
* **Armazenamento**
* **Rede**
* **Aplicativo**

O status em cada categoria é um resumo de métricas individuais; se qualquer métrica em uma categoria estiver no estado crítico, a categoria inteira estará em um estado crítico para a finalidade da página de visão geral. O mesmo resumo pode ser visualizado em um nível de ambiente e em um nível de instância.

![](assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Por padrão, ao navegar para essa página, as instâncias do ambiente de produção são visíveis, mas outros ambientes também podem ser abertos.

## Tutorial em vídeo {#video-tutorial}

### Visão geral dos relatórios do Cloud Manager {#reports-video}

Os Relatórios do Cloud Manager fornecem uma visualização dos Ambientes do Programa e das instâncias de AEM por meio de um conjunto de gráficos que informam e rastreiam várias métricas para cada instância de AEM.
Consulte o vídeo abaixo para obter mais detalhes.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)

## Detalhes do monitoramento do sistema {#system-monitoring-detail}

Para exibir os detalhes de métricas específicas, você pode clicar em uma das categorias na navegação à esquerda ou clicar em um dos indicadores de categoria para uma instância específica. Cada página de detalhes mostra uma série de gráficos para as métricas dentro dessa categoria. Você pode exibir as métricas de todas as instâncias em um ambiente ou para uma instância específica. Você pode alternar entre o ambiente e as instâncias usando as caixas suspensas no canto superior direito.

![](assets/System_Monitoring1.png)

A navegação à esquerda mostrará as métricas disponíveis na categoria selecionada no momento, para as quais há dados para o ambiente e as instâncias selecionadas no momento.

![](assets/System_Monitoring2.png)

Um gráfico individual mostrará o status e um gráfico dos dados ao longo do tempo, juntamente com os limites. Se várias instâncias forem exibidas, os dados de cada instância serão em uma série separada.

![](assets/Monitoring_Graphs1.png)

As séries individuais podem ser ocultadas em um gráfico clicando nas séries na legenda.
Por exemplo, se você clicar na série de limites de aviso, verá apenas o limite crítico.

![](assets/Monitoring_Graphs2.png)

### Definições de Métricas {#metric-definitions}

**Host**

* Carregar por núcleo: o número de processos que estão sendo executados pela CPU ou que estão em um estado de espera em média por um período de um (carga1), cinco (carga5) e quinze (carga15) minutos.
* Contagem de Processos: o número de processos abertos no momento.
* Contagem de usuários: o número de usuários com uma sessão de shell ativa.
* Uso de memória: a porcentagem da memória do sistema alocada no momento.
* Memória JVM (heap): o tamanho (em Megabytes) do Java Heap alocado.
* Espaço De Geração Antigo: a porcentagem de memória de geração antiga da JVM alocada atualmente.

**Rede**

* Verificação da porta CQ: O tempo de resposta em segundos para acessar a porta do AEM ou Dispatcher. Há métricas diferentes para autor, publicação e dispatcher.

**Armazenamento**

* Espaço em disco: O espaço em disco usado (em Megabytes) para cada ponto de montagem no host. Há métricas diferentes para cada ponto de montagem. No mínimo, você verá métricas para &quot;/&quot; e &quot;/mnt&quot;, mas métricas de ponto de montagem adicionais podem estar disponíveis, dependendo da configuração específica da instância.
* Tamanho da pasta: AEM armazenamento de segmentos: O espaço em disco usado (em Gigabytes) para a Loja de Segmentos de AEM.

**Aplicativo**

* Agente de replicação: O tempo, em segundos, para um evento de replicação de teste. Há métricas separadas para cada agente de replicação.
* Liberação do Dispatcher: O número de itens atualmente na fila de liberação do dispatcher.

## Relatórios de SLA {#sla-reporting}

Os clientes podem ver o desempenho de seu ambiente de produção AEM em relação ao Contrato de nível de serviço (SLA). Isso está disponível por meio de um submenu na tela Relatórios .
Por exemplo, o gráfico abaixo mostra o nível mensal de SLA para 2018.

![](assets/SLA-Reports-one.png)

Assim como nos gráficos de monitoramento do sistema, o acumulado em um ponto de dados mostra os valores específicos daquele mês.

![](assets/SLA-Reports-two.png)

A seção Análise de eventos neste gráfico mostra o conjunto de incidentes que ocorreram para o programa durante o ano selecionado atualmente. Cada incidente tem um intervalo de tempo, uma causa e um conjunto de comentários.

![](assets/sla-reporting3.png)

## Métricas de SLA {#sla-metrics}

* **Contrato** do autor: Este é o SLA definido em seu contrato com o Adobe Managed Services para o nível de criação.

* **SLA** do autor do AMS: Esse é o tempo de atividade medido dos incidentes de fatoração do nível do autor de produção causados pelo Adobe ou por nossos fornecedores.

* **SLA** do autor: Esse é o tempo de atividade medido do nível de criação ignorando o tempo de inatividade programado, como janelas de manutenção.

* **Contrato** de usuário final: Este é o SLA definido em seu contrato com o Adobe Managed Services para o nível de publicação.

* **SLA** do usuário final do AMS: Esse é o tempo de atividade medido dos incidentes de fatoração do nível de publicação de produção causados pelo Adobe ou por nossos fornecedores.

* **SLA** do Usuário Final: Esse é o tempo de atividade medido do nível de publicação ignorando o tempo de inatividade programado, como janelas de manutenção.