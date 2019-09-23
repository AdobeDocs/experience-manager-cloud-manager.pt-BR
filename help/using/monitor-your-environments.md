---
title: Monitore seus ambientes
seo-title: Monitore seus ambientes
description: 'null'
seo-description: Siga esta página para saber mais sobre o Monitoramento do sistema no Gerenciador de nuvem que é feito observando as instâncias individuais em um ambiente e rastreando várias métricas para cada instância.
translation-type: tm+mt
source-git-commit: 548d18f251cf8c4c827d2208fec04cde235ce731

---


# Monitoramento do sistema {#system-monitoring}

O monitoramento do sistema em [!UICONTROL Cloud Manager] é feito observando as instâncias individuais em um ambiente e rastreando várias métricas para cada instância. Cada métrica tem dois limites definidos - um limite *de* aviso e um limite ** crítico.

Se uma métrica ultrapassar o seu limite crítico, considera-se que se encontra num estado crítico; se uma métrica estiver acima de seu limite de aviso (mas abaixo de seu limite crítico), ela será considerada como estando em um estado de aviso. Os limites são definidos pelo Adobe Managed Services e podem ser visualizados em [!UICONTROL Cloud Manager]. Na maioria dos casos, os limites são consistentes entre os clientes, mas há casos em que o Adobe Managed Services modificará os limites para atender às necessidades específicas do cliente. As perguntas sobre os limites devem ser direcionadas ao engenheiro de sucesso do cliente (CSE).

## Navegação até o monitoramento do sistema {#navigating-system-monitoring}

Navegar até o recurso Monitoramento do sistema pode ser feito de duas formas.

1. Faça logon na página de aterrissagem Serviços **gerenciados - Programas** .

   ![](assets/ProgramLanding.png)

1. Clique no terceiro ícone no cartão do programa.

   ![](assets/program-card.png)

   *Ou*,

* Navegue até a página de aterrissagem Monitoramento **do** Sistema pelo item de menu de navegação global **Relatórios** dentro [!UICONTROL Cloud Manager].


## Página Visão geral do monitoramento do sistema {#system-monitoring-overview-page}

A página Visão geral do monitoramento do sistema lista os ambientes monitorados no programa e relata sobre sua integridade de alto nível em quatro categorias separadas:

* **Host**
* **Armazenamento**
* **Rede**
* **Aplicativo**

O status em cada categoria é um resumo de métricas individuais - se qualquer métrica em uma categoria estiver no estado crítico, a categoria inteira estará em estado crítico para a finalidade da página de visão geral. O mesmo resumo pode ser visualizado em nível de ambiente e instância.

![](assets/Reports.png)

>[!NOTE]
>
>Por padrão, ao navegar até essa página, as instâncias do ambiente de produção ficam visíveis, mas outros ambientes também podem ser abertos.

## Detalhes do monitoramento do sistema {#system-monitoring-detail}

Para exibir os detalhes de métricas específicas, você pode clicar em uma das categorias na navegação à esquerda ou clicar em um dos indicadores de categoria para uma instância específica. Cada página de detalhes mostra uma série de gráficos para as métricas dentro dessa categoria. Você pode exibir as métricas para todas as instâncias em um ambiente ou para uma instância específica. Você pode alternar entre o ambiente e as instâncias usando as caixas suspensas no canto superior direito.

![](assets/System_Monitoring1.png)

A navegação à esquerda mostrará as métricas disponíveis na categoria atualmente selecionada para as quais há dados para o ambiente e as instâncias selecionadas.

![](assets/System_Monitoring2.png)

Um gráfico individual mostrará o status e um gráfico dos dados ao longo do tempo, juntamente com os limites. Se várias instâncias forem exibidas, os dados de cada instância estarão em uma série separada.

![](assets/Monitoring_Graphs1.png)

Uma série individual pode ser ocultada em um gráfico ao clicar na série na legenda.
Por exemplo, se você clicar na série de limites de aviso, verá apenas o limite crítico.

![](assets/Monitoring_Graphs2.png)

### Definições de métrica {#metric-definitions}

**Host**

* Carregar por núcleo: o número de processos que estão sendo executados pela CPU ou que estão em um estado de espera, em média, em um período de um (load1), cinco (load5) e quinze (load15) minutos.
* Contagem de processos: o número de processos atualmente abertos.
* Contagem de usuários: o número de usuários com uma sessão de shell ativa.
* Uso de memória: a porcentagem da memória do sistema alocada no momento.
* Memória JVM (heap): o tamanho (em Megabytes) do Java Heap alocado.
* Espaço de geração antiga: a porcentagem da memória JVM Old Generation alocada no momento.

**Rede**

* Verificação da porta CQ: O tempo de resposta em segundos para acessar a porta do AEM ou Dispatcher. Há métricas diferentes para autor, publicação e despachante.

**Armazenamento**

* Espaço em disco: O espaço em disco usado (em Megabytes) para cada ponto de montagem no host. Há métricas diferentes para cada ponto de montagem. No mínimo, você verá métricas para "/" e "/mnt", mas métricas adicionais de ponto de montagem podem estar disponíveis dependendo da configuração específica da instância.
* Tamanho da pasta: Armazenamento de segmentos do AEM: O espaço em disco usado (em Gigabytes) para o AEM Segment Store.

**Aplicativo**

* Agente de Replicação: O tempo, em segundos, para um evento de replicação de teste. Há métricas separadas para cada agente de replicação.
* Liberação do Dispatcher: O número de itens atualmente na fila de despachantes.

## Relatórios de SLA {#sla-reporting}

Os clientes podem ver o desempenho de seu ambiente de produção do AEM em relação ao SLA (Service Level Agreement, contrato de nível de serviço). Isso está disponível por meio de um submenu na tela Relatórios.
Por exemplo, o gráfico abaixo mostra o nível de SLA mensal para 2018.

![](assets/sla-reporting1.png)

Assim como nos gráficos de monitoramento do sistema, rolar sobre um ponto de dados mostra os valores específicos para esse mês.

![](assets/sla-reporting2.png)

A seção Análise de eventos neste gráfico mostra o conjunto de incidentes que ocorreram no programa durante o ano selecionado. Cada incidente tem um intervalo de tempo, uma causa e um conjunto de comentários.

![](assets/sla-reporting3.png)

## Métricas de SLA {#sla-metrics}

* **Contrato** do autor: Este é o SLA definido em seu contrato com o Adobe Managed Services para a camada do autor.

* **SLA** do autor do AMS: Esse é o tempo de atividade medido dos incidentes de factoring de nível do autor da produção causados pela Adobe ou por nossos fornecedores.

* **SLA** do autor: Esse é o tempo de atividade medido da camada do autor ignorando o tempo de inatividade programado, como janelas de manutenção.

* **Contrato** do usuário final: Este é o SLA definido em seu contrato com os Serviços gerenciados da Adobe para a camada de publicação.

* **SLA** do usuário final do AMS: Esse é o tempo de atividade medido dos incidentes de factoring de nível de publicação de produção causados pela Adobe ou por nossos fornecedores.

* **SLA** do usuário final: Esse é o tempo de atividade medido da camada de publicação ignorando o tempo de inatividade programado, como janelas de manutenção.