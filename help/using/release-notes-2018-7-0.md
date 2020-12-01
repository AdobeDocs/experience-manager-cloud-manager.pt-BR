---
title: Notas da versão 2018.7.0
seo-title: Notas da versão 2018.7.0
description: 'null'
seo-description: Siga esta página para obter informações sobre a versão 2018.7.0 do Cloud Manager.
uuid: d7b49e32-01dc-48ce-b744-e6a806fbdd8a
contentOwner: jsyal
topic-tags: release-notes
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b64bf9ab-27ed-4f33-adc8-d73d34094f1b
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 5%

---


# Notas da versão 2018.7.0 {#release-notes-for}

A seção a seguir descreve a versão [!UICONTROL Cloud Manager] 2018.7.0 que oferece o recurso *autoescala*.

**O dimensionamento** automático é habilitado por meio da escalação horizontal de  `Dispatcher/Publish` segmentos no ambiente de produção para suportar um aumento brusco na carga, no volume, no acesso e em outras métricas monitoradas definidas.

## Data de lançamento {#release-date}

A data de lançamento da versão 2018.7.0 [!UICONTROL Cloud Manager] é 10 de setembro de 2018.

## Novidades {#what-s-new}

* **Provisionamento**  -  [!UICONTROL Cloud Manager] agora terá a capacidade de dimensionar automaticamente o ambiente de produção no programa do cliente, dimensionando horizontalmente para menos com segmentos do Dispatcher/Publish. A novidade na interface do usuário é a seção Provisionamento na Configuração do Programa que será exibida se o dimensionamento automático estiver ativado no programa do cliente. Consulte [Configure seu Programa](setting-up-program.md) para saber mais.

* **Ambientes**  - Agora é possível ver uma visualização detalhada de ambientes de Produção e Estágio juntamente com o tamanho, o armazenamento, a região e o status dos nós associados a cada ambiente. Consulte [Gerenciar seus Ambientes](manage-your-environment.md) para saber mais.

* **Análise**  de qualidade de código - Nova regra para identificar o uso incorreto da API. Consulte [Regras de qualidade de código personalizadas](custom-code-quality-rules.md) para saber mais.

* **Teste**  de desempenho - Ao visualizar os resultados do teste de desempenho, estão disponíveis os gráficos de Utilização da CPU, Tempo de espera de E/S do disco, Taxa de erro da página, Utilização da largura de banda do disco, Utilização da largura de banda da rede, Tempo de resposta de página de pico e 95% do tempo de resposta da página. Consulte a seção *Teste de desempenho* na página [Entender os resultados do teste](understand-your-test-results.md).

* **Teste**  de desempenho - Durante a exibição dos resultados do teste de desempenho, é possível baixar a lista de erros de página e solicitações lentas. Consulte a seção *Teste de desempenho* na página [Entender os resultados do teste](understand-your-test-results.md).

## Correções de erros {#bug-fixes}

* Em determinadas circunstâncias, a sincronização interna do sistema falhou inadequadamente, resultando em visualizações inconsistentes de dados.
* Em alguns casos, o acionador de pipeline manual não foi selecionado automaticamente, resultando em problemas de validação de formulário.
* Scripts específicos de compilação do cliente podem causar falhas durante a etapa de compilação com base nas incompatibilidades do plug-in.

## Problemas conhecidos {#known-issues}

* Embora os clientes possam selecionar o acionador de confirmação, o pipeline pode não ser start com base em novos compromissos.
* A barra lateral de notificação [!UICONTROL Experience Cloud] pode não carregar as notificações de forma consistente. No entanto, as notificações estão visíveis no [!UICONTROL Experience Cloud] e, se configuradas, ainda serão enviadas por email.

