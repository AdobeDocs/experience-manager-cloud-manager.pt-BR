---
title: Notas da versão 2018.7.0
seo-title: Notas da versão 2018.7.0
description: Saiba mais sobre a versão 2018.7.0 do Cloud Manager
seo-description: Siga esta página para obter informações sobre o Cloud Manager Versão 2018.7.0.
uuid: d7b49e32-01dc-48ce-b744-e6a806fbdd8a
contentOwner: jsyal
topic-tags: release-notes
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b64bf9ab-27ed-4f33-adc8-d73d34094f1b
feature: Informações da versão
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 12%

---


# Notas da versão 2018.7.0 {#release-notes-for}

A seção a seguir descreve a versão [!UICONTROL Cloud Manager] 2018.7.0 que fornece o recurso de *dimensionamento automático*.

**O dimensionamento automático é ativado por meio da escala horizontal dos segmentos do no ambiente de produção para suportar um aumento brusco na carga, volume, acesso e outras métricas monitoradas definidas.**`Dispatcher/Publish`

## Data de lançamento {#release-date}

A Data de lançamento da versão [!UICONTROL Cloud Manager] 2018.7.0 é 10 de setembro de 2018.

## Novidades {#what-s-new}

* **Provisionamento**  -  [!UICONTROL Cloud Manager] agora terá a capacidade de dimensionar automaticamente o ambiente de produção no programa do cliente ao dimensionar horizontalmente com segmentos do Dispatcher/Publish. Uma novidade na interface do usuário é a seção Provisionamento na configuração do programa que será exibida se o dimensionamento automático estiver ativado no programa do cliente. Consulte [Configure seu programa](setting-up-program.md) para saber mais.

* **Ambientes**  - Agora é possível ver uma visualização detalhada dos ambientes de Produção e Estágio, juntamente com o tamanho, o armazenamento, a região e o status dos nós associados a cada ambiente. Consulte [Gerenciar seus ambientes](manage-your-environment.md) para saber mais.

* **Análise de qualidade do código**  - Nova regra para identificar o uso incorreto da API. Consulte [Regras de qualidade de código personalizadas](custom-code-quality-rules.md) para saber mais.

* **Teste de desempenho**  - Ao visualizar os resultados dos testes de desempenho, estão disponíveis gráficos de utilização da CPU, Tempo de espera da E/S do disco, Taxa de erro da página, Utilização da largura de banda do disco, Utilização da largura de banda da rede, Tempo de resposta de página de pico e 95% do tempo de resposta da página de percentual. Consulte a seção *Teste de desempenho* na página [Entender os resultados de teste](understand-your-test-results.md).

* **Teste de desempenho**  - ao visualizar os resultados do teste de desempenho, é possível baixar a lista de erros de página e de solicitações lentas. Consulte a seção *Teste de desempenho* na página [Entender os resultados de teste](understand-your-test-results.md).

## Correções de erros {#bug-fixes}

* Em determinadas circunstâncias, a sincronização interna do sistema falhou inadequadamente, levando a visualizações inconsistentes dos dados.
* Em alguns casos, o acionador de pipeline manual não foi selecionado automaticamente, levando a problemas de validação de formulário.
* Scripts específicos de criação de clientes podem causar falhas durante a etapa de criação com base em incompatibilidades de plug-in.

## Problemas conhecidos {#known-issues}

* Embora os clientes possam selecionar o acionador de confirmação, o pipeline pode não começar realmente com base em novos commits.
* A barra lateral de notificação [!UICONTROL Experience Cloud] pode não carregar as notificações de forma consistente. As notificações, no entanto, estão visíveis no [!UICONTROL Experience Cloud] e, se configuradas, ainda serão enviadas por email.

