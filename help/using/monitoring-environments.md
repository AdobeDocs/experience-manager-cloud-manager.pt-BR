---
title: Monitoramento de ambientes
description: Saiba como monitorar seus ambientes no Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 5907ca6337d33c26ff19a14bfeb358cd9f7b935d
workflow-type: ht
source-wordcount: '933'
ht-degree: 100%

---


# Monitoramento de ambientes {#monitoring-environments}

Saiba como monitorar seus ambientes no Cloud Manager.

## Limites de métrica {#thresholds}

O monitoramento do sistema no [!UICONTROL Cloud Manager] é feito observando as instâncias individuais em um ambiente e rastreando diversas métricas de cada instância. Cada métrica tem dois limites definidos: um limite de aviso e um limite crítico.

Se uma métrica ultrapassar seu limite crítico, ela será considerada em estado crítico. Se uma métrica ultrapassar seu limite de aviso (mas estiver abaixo do limite crítico), ela será considerada em estado de aviso. Os limites são definidos pelo Adobe Managed Services e podem ser visualizados no [!UICONTROL Cloud Manager]. Na maioria dos casos, os limites são consistentes entre os clientes, mas há casos em que o Adobe Managed Services modificará os limites para atender às necessidades específicas do cliente. Dúvidas sobre os limites devem ser direcionadas ao seu engenheiro de sucesso do cliente (CSE).

## Acesso ao monitoramento do sistema {#accessing-system-monitoring}

Siga estas etapas para acessar o monitoramento do sistema.

1. Faça logon na página de destino **Managed Services - Programas**.

   ![Programas do Managed Services](/help/assets/ProgramLanding.png)

1. Clique no quarto ícone no cartão do programa.

   ![Configurações](/help/assets/first-timea1.png)


Como alternativa, é possível navegar até a página de destino **Monitoramento de sistema** por meio do item do menu de navegação global **Relatórios**, no [!UICONTROL Cloud Manager].

## Visão geral do monitoramento do sistema {#system-monitoring-overview}

A página de visão geral do Monitoramento do sistema lista os ambientes monitorados no programa e produz relatórios sobre sua integridade de alto nível em quatro categorias separadas:

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

Para exibir os detalhes de métricas específicas, é possível clicar em uma das categorias na navegação à esquerda ou clicar em um dos indicadores de categoria para uma instância específica. Cada página de detalhes mostra uma série de gráficos para as métricas contidas nessa categoria. É possível exibir as métricas de todas as instâncias em um ambiente ou para uma instância específica. Você pode alternar entre o ambiente e as instâncias usando as caixas suspensas no canto superior direito.

![Selecionar ambiente](/help/assets/System_Monitoring1.png)

A navegação à esquerda mostrará as métricas disponíveis da categoria selecionada para as quais há dados para o ambiente e as instâncias selecionadas no momento.

![Métricas de monitoramento](/help/assets/System_Monitoring2.png)

Um gráfico individual mostrará o status e um gráfico dos dados ao longo do tempo, juntamente com os limites. Se várias instâncias forem exibidas, os dados de cada instância estarão em uma série separada.

![Gráfico de métricas](/help/assets/Monitoring_Graphs1.png)

As séries individuais podem ser ocultadas em um gráfico clicando nelas na legenda.
Por exemplo, se você clicar na série de limites de aviso, apenas o limite crítico será exibido.

![Gráfico de modificação](/help/assets/Monitoring_Graphs2.png)

### Definições de métricas {#metric-definitions}

#### Host {#host}

* **Carregar por núcleo**: a média de processos que estão sendo executados pela CPU ou que estão em um estado de espera para um período de um (load1), cinco (load5) e quinze (load15) minutos
* **Contagem de processos**: o número de processos atualmente abertos
* **Contagem de usuários**: o número de usuários com uma sessão de shell ativa
* **Uso de memória**: a porcentagem de memória do sistema alocada no momento
* **Memória JVM**: o tamanho (em megabytes) do heap Java alocado
* **Espaço de antiga geração**: a porcentagem de memória de JVM de antiga geração atualmente alocada

#### Rede {#network}

* **Verificação de porta CQ**: o tempo de resposta em segundos para acessar a porta do AEM ou do Dispatcher
   * Existem métricas diferentes para criação, publicação e Dispatcher.

#### Armazenamento {#storage}

* **Espaço em disco**: o espaço em disco usado (em megabytes) para cada ponto de montagem no host
   * Existem métricas diferentes para cada ponto de montagem.
   * No mínimo, devem existir métricas para `/` e `/mnt`. Porém, métricas de ponto de montagem adicionais podem estar disponíveis, dependendo da configuração específica da instância.
* **Tamanho da pasta**
* **Loja de segmentos do AEM**: o espaço em disco usado (em gigabytes) para a Loja de segmentos do AEM

#### Aplicativo {#application}

* **Agente de replicação**: o tempo (em segundos) para um evento de replicação de teste
   * Existem métricas separadas para cada agente de replicação.
* **Limpeza do Dispatcher**: o número de itens atualmente na fila de limpeza do Dispatcher

## Relatórios de SLA {#sla-reporting}

Os clientes podem ver o desempenho de seu ambiente de produção do AEM em relação ao contrato de nível de serviço (SLA). Isso está disponível por meio de um submenu na tela **Relatórios**.

O gráfico a seguir mostra o nível mensal de SLA para 2018.

![Gráfico SLA de 2018](/help/assets/SLA-Reports-one.png)

Assim como nos gráficos de monitoramento do sistema, rolar sobre um ponto de dados mostra os valores específicos daquele mês.

![Rolagem do ponto de dados](/help/assets/SLA-Reports-two.png)

A seção **Análise de evento** deste gráfico mostra a série de incidentes que ocorreram para o programa durante o ano selecionado. Cada incidente tem um intervalo de tempo, uma causa e um conjunto de comentários.

![Análise de evento](/help/assets/sla-reporting3.png)

## Métricas de SLA {#sla-metrics}

* **Contrato de autor**: este é o SLA definido em seu contrato com o Adobe Managed Services para o nível de criação.
* **SLA de autor do AMS**: esse é o tempo de atividade total de incidentes considerados no nível do autor de produção que foram causados pela Adobe ou por nossos fornecedores.
* **SLA do autor**: esse é o tempo de atividade total pelo qual o nível de criação ignorou o tempo de inatividade programado, como as janelas de manutenção.
* **Contrato de usuário final**: esse é o SLA definido em seu contrato com o Adobe Managed Services para o nível de publicação.
* **SLA de usuário final do AMS**: esse é o tempo de atividade total de incidentes considerados no nível de publicação de produção que foram causados pela Adobe ou por nossos fornecedores.
* **SLA de usuário final**: esse é o tempo de atividade total pelo qual o nível de publicação ignorou o tempo de inatividade programado, como as janelas de manutenção.

## Tutorial em vídeo {#video-tutorial}

Este vídeo fornece uma visão geral do uso dos gráficos produzidos pelos relatórios do Cloud Manager para uma visualização nos ambientes do programa.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
