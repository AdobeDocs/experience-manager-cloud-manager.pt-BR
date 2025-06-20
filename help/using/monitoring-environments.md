---
title: Monitorar ambientes
description: Saiba como monitorar os seus ambientes no Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 74%

---


# Monitorar ambientes {#monitoring-environments}

Saiba como monitorar os seus ambientes no Cloud Manager.

## Limites de métrica {#thresholds}

O monitoramento do sistema no [!UICONTROL Cloud Manager] é feito observando as instâncias individuais em um ambiente e rastreando as diversas métricas de cada instância. Cada métrica tem dois limites definidos: um limite de *aviso* e um limite *crítico*.

Se uma métrica ultrapassar seu limite de aviso (mas estiver abaixo do limite crítico), ela será considerada em estado de aviso.

Se uma métrica ultrapassar seu limite crítico, ela será considerada em estado crítico.

O Adobe Managed Services define os limites, que você pode ver no [!UICONTROL Cloud Manager]. Na maioria dos casos, os limites são consistentes entre os clientes, mas há casos em que o Adobe Managed Services modificará os limites para atender às necessidades específicas do cliente. Encaminhe qualquer dúvida sobre os limites para o seu engenheiro de sucesso do cliente (CSE).

## Acessar monitoramento do sistema {#accessing-system-monitoring}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selecione a organização e o programa apropriados.

1. Clique no ícone ![Mais, reticências](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) do programa que você deseja monitorar.
1. No menu, em **Gerenciar**, clique em **Mostrar Monitoramento** para abrir a página **Relatórios** que mostra as informações de monitoramento do sistema.

   ![Configurações](/help/assets/first-timea1.png)

.

## Visão geral do monitoramento do sistema {#system-monitoring-overview}

A seção **Monitoramento do sistema** da página **Relatórios** lista os ambientes monitorados no programa. Ela relata a integridade de alto nível nas quatro categorias a seguir:

* Host
* Armazenamento
* Rede
* Aplicativo

O status em cada categoria é um resumo de métricas individuais. Se alguma métrica em uma categoria estiver em estado crítico, a categoria inteira será considerada em estado crítico pela página de visão geral. O mesmo resumo pode ser visualizado em um nível de ambiente e em um nível de instância.

![Visão geral do monitoramento do sistema](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Por padrão, ao navegar para essa página, as instâncias do ambiente de produção são visíveis, mas outros ambientes também podem ser visualizados.

## Detalhes do monitoramento do sistema {#system-monitoring-detail}

Para exibir os detalhes de métricas específicas, clique em uma das colunas de categoria de uma instância específica ou no título da categoria na navegação à esquerda. Cada página de detalhes mostra uma série de gráficos para as métricas contidas nessa categoria. É possível exibir as métricas de todas as instâncias em um ambiente ou para uma instância específica. Você pode alternar entre o ambiente e as instâncias usando as caixas suspensas no canto superior direito.

![Selecionar ambiente](/help/assets/System_Monitoring1.png)

A navegação à esquerda mostrará as métricas disponíveis da categoria selecionada para as quais há dados para as instâncias e o ambiente selecionados no momento.

Um gráfico individual mostra o status e um gráfico dos dados ao longo do tempo, juntamente com os limites. Se várias instâncias forem exibidas, os dados de cada instância estarão em uma série separada.

![Gráfico de métricas](/help/assets/Monitoring_Graphs1.png)

As séries individuais podem ser ocultadas em um gráfico clicando nelas na legenda.
Por exemplo, ao clicar na série de limites de aviso, você verá apenas o limite crítico.

![Modificação do gráfico](/help/assets/Monitoring_Graphs2.png)

### Definições de métricas {#metric-definitions}

#### Host {#host}

* **`Load Per Core`**: o número de processos que o CPU está executando. Ou, a média do número de processos enfileirados que estão em um estado de espera para um período de um (load1), cinco (load5) e quinze (load15) minutos.
* **P`rocess Count`**: o número de processos atualmente abertos.
* **`User Count`**: o número de usuários com uma sessão de shell ativa.
* **`Memory Usage`**: a porcentagem de memória do sistema alocada no momento.
* **`JVM Memory`**: O tamanho (em megabytes) do heap Java alocado.
* **`Old Generation Space`**: a porcentagem de memória JVM de antiga geração atualmente alocada.

#### Rede {#network}

* **`CQ Port Check`**: o tempo de resposta em segundos para acessar a porta do AEM ou do Dispatcher. Existem métricas diferentes para criação, publicação e Dispatcher.

#### Armazenamento {#storage}

* **`Disk Space`**: O espaço em disco usado (em megabytes) para cada ponto de montagem no host. Existem métricas diferentes para cada ponto de montagem. No mínimo, devem existir métricas para `/` e `/mnt`, as métricas de ponto de montagem adicionais podem estar disponíveis, dependendo da configuração específica da instância.
* **`Folder Size`**
* **`AEM Segment Store`**: o espaço em disco usado (em gigabytes) para o Repositório de Segmentos do AEM.

#### Aplicativo {#application}

* **`Replication Agent`**: O tempo (em segundos) para um evento de replicação de teste
   * Existem métricas separadas para cada agente de replicação.
* **`Dispatcher Flush`**: o número de itens atualmente na fila de liberação do Dispatcher

## Relatórios de SLA {#sla-reporting}

É possível ver o desempenho do ambiente de produção do AEM em relação ao contrato de nível de serviço (SLA).

O gráfico a seguir mostra o nível mensal de SLA para 2019.

![Gráfico SLA de 2018](/help/assets/SLA-Reports-one.png)

Assim como nos gráficos de monitoramento do sistema, rolar sobre um ponto de dados mostra os valores específicos daquele mês.

![Rolagem do ponto de dados](/help/assets/SLA-Reports-two.png)

A seção **Análise de evento** deste gráfico mostra a série de incidentes que ocorreram para o programa durante o ano selecionado. Cada incidente tem um intervalo de tempo, uma causa e um conjunto de comentários.

![Análise de evento](/help/assets/sla-reporting3.png)

## Métricas de SLA {#sla-metrics}

* **`Author Contract`**: o SLA definido em seu contrato com o Adobe Managed Services para a camada de criação.
* **`AMS Author SLA`**: O tempo de atividade medido no nível de criação de produção, considerando incidentes causados por fornecedores ou pela Adobe.
* **`Author SLA`**: O tempo de atividade medido no nível de criação ignorou o tempo de inatividade programado, como as janelas de manutenção.
* **`End User Contract`**: o SLA definido em seu contrato com o Adobe Managed Services para o nível de publicação.
* **`AMS End User SLA`**: As uptimes medidas do nível de publicação de produção, considerando incidentes causados por fornecedores ou pela Adobe.
* **`End User SLA`**: O tempo de atividade medido no nível de publicação ignorou o tempo de inatividade agendado, como as janelas de manutenção.

## Tutorial em vídeo {#video-tutorial}

Este vídeo fornece uma visão geral do uso dos gráficos produzidos pelos relatórios do Cloud Manager para que você possa visualizar os ambientes do programa.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
