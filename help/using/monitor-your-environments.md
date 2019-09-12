---
title: Monitorar seus ambientes
seo-title: Monitorar seus ambientes
description: 'null'
seo-description: Siga esta página para saber mais sobre o Monitoramento do sistema no Experience Manager Manager que é feito observando as instâncias individuais em um ambiente e rastreando várias métricas para cada instância.
translation-type: tm+mt
source-git-commit: 548d18f251cf8c4c827d2208fec04cde235ce731

---


# Monitoramento do sistema {#system-monitoring}

O Monitoramento do sistema é [!UICONTROL Cloud Manager] feito observando as instâncias individuais em um ambiente e rastreando várias métricas para cada instância. Cada métrica tem dois limites definidos - um *limite de aviso* e um limite *crítico*.

Se uma métrica ultrapassar seu limite crítico, considerada como estando em um estado crítico; se uma métrica ultrapassar seu limite de aviso (mas abaixo do limite crítico), considerada como estando em um estado de aviso. Os limites são definidos pelo Adobe Managed Services e podem ser visualizados [!UICONTROL Cloud Manager]. Na maioria dos casos, os limites são consistentes entre os clientes, mas há casos em que o Adobe Managed Services modificará os limites para corresponder a requisitos específicos do cliente. As perguntas sobre os limites devem ser direcionadas ao seu Engenheiro de sucesso do cliente (CSE).

## Navegação para monitoramento do sistema {#navigating-system-monitoring}

A navegação para o recurso Monitoramento do sistema pode ser feita de duas formas.

1. Faça logon em **Serviços gerenciados - Página** de aterrissagem dos Programas.

   ![](assets/ProgramLanding.png)

1. Clique no terceiro ícone no cartão de programas.

   ![](assets/program-card.png)

   *Ou*,

* Navegue até a página **inicial do Monitoramento** do sistema através do **item** de menu de navegação global Relatórios.[!UICONTROL Cloud Manager]


## Página de visão geral do monitoramento do sistema {#system-monitoring-overview-page}

A página Visão geral do monitoramento do sistema lista os ambientes monitorados no programa e relatórios sobre sua saúde de alto nível em quatro categorias separadas:

* **Host**
* **Armazenamento**
* **Rede**
* **Aplicativo**

O status em cada categoria é um resumo das métricas individuais - se qualquer métrica em uma categoria estiver no estado crítico, a categoria inteira estará em um estado crítico para a finalidade da página de visão geral. A mesma amostra pode ser visualizada em nível de ambiente e em nível de instância.

![](assets/Reports.png)

>[!NOTE]
>
>Por padrão, ao navegar para essa página, as instâncias do ambiente de produção são visíveis, mas outros ambientes também podem ser abertos.

## Detalhe de monitoramento do sistema {#system-monitoring-detail}

Para exibir os detalhes de métricas específicas, clique em uma das categorias na navegação esquerda ou clique em um dos indicadores de categoria para uma instância específica. Cada página de detalhes mostra uma série de gráficos para as métricas dentro dessa categoria. Você pode exibir as métricas para todas as instâncias em um ambiente ou para uma instância específica. É possível alternar entre o ambiente e as instâncias usando as caixas suspensas no canto superior direito.

![](assets/System_Monitoring1.png)

A navegação à esquerda mostrará as métricas disponíveis na categoria selecionada no momento para as quais há dados para o ambiente e as instâncias atualmente selecionados.

![](assets/System_Monitoring2.png)

Um gráfico individual mostrará o status e um gráfico dos dados ao longo do tempo juntamente com os limites. Se várias instâncias forem exibidas, os dados de cada instância estarão em uma série separada.

![](assets/Monitoring_Graphs1.png)

As séries individuais podem ficar ocultas em um gráfico clicando na série na legenda.
Por exemplo, se você clicar na série de limite de aviso, verá apenas o limite crítico.

![](assets/Monitoring_Graphs2.png)

### Definições de métricas {#metric-definitions}

**Host**

* Carregar por Core: o número de processos que estão sendo executados pela CPU ou que estão em um estado aguardado em relação a um período de um (load 1), cinco (carregar 5) e quinze (carregar 15) período.
* Contagem de processos: o número de processos abertos no momento.
* Contagem do usuário: o número de usuários com uma sessão de shell ativa.
* Uso de memória: a porcentagem da memória do sistema alocada atualmente.
* Memória JVM (heap): o tamanho (em Megabytes) do Java Heap alocado.
* Espaço de geração antigo: a porcentagem da memória JVM Old Generation alocada atualmente.

**Rede**

* Verificação de porta do CQ: O tempo de resposta em segundos para acessar a porta AEM ou Dispatcher. Há diferentes métricas para autor, publicação e dispatcher.

**Armazenamento**

* Espaço em disco: O espaço em disco usado (em Megabytes) para cada ponto de montagem no host. Há diferentes métricas para cada ponto de montagem. No mínimo, você verá métricas para "/" e "/mnt", mas outras métricas de ponto de montagem podem estar disponíveis dependendo da configuração de instância específica.
* Tamanho da pasta: Loja de segmentos do AEM: O espaço em disco usado (em Gigabytes) para a Loja de segmentos do AEM.

**Aplicativo**

* Agente de replicação: O tempo, em segundos, para um evento de replicação de teste. Há métricas distintas para cada agente de replicação.
* Flush do Dispatcher: O número de itens na fila flush do dispatcher.

## Relatórios SLA {#sla-reporting}

Os clientes podem ver o desempenho do ambiente AEM de produção em relação ao Contrato de nível de serviço (SLA) contratado. Isso está disponível por meio de um submenu na tela Relatórios.
Por exemplo, o gráfico abaixo mostra o resultado mensal SLA de 2018.

![](assets/sla-reporting1.png)

Assim como ocorre com os gráficos de monitoramento do sistema, a passagem sobre um ponto de dados mostra os valores específicos desse mês.

![](assets/sla-reporting2.png)

A seção Análise de evento neste gráfico mostra o conjunto de incidentes que ocorreram no programa durante o ano selecionado. Cada incidente tem um intervalo de tempo, uma causa e um conjunto de comentários.

![](assets/sla-reporting3.png)

## Métricas SLA {#sla-metrics}

* **Contrato de autor**: Esse é o SLA definido no seu contrato com os Serviços gerenciados da Adobe para o nível do autor.

* **SLA do autor de AMS**: Esse é o tempo medido medido dos incidentes de fatoramento de nível de produção causado pela Adobe ou pelos fornecedores.

* **SLA do autor**: Esse é o tempo medido medido do nível do autor ignorando o tempo de inatividade programado, como janelas de manutenção.

* **Contrato de usuário final**: Esse é o SLA definido no seu contrato com os Serviços gerenciados da Adobe para o nível de publicação.

* **SLA do usuário final AMS**: Esse é o tempo medido medido dos incidentes de publicação de nível de publicação de produção causado pela Adobe ou pelos fornecedores.

* **SLA do usuário final**: Esse é o tempo medido medido do nível de publicação ignorando o tempo de inatividade programado, como janelas de manutenção.