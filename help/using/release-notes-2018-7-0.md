---
title: Notas de versão de 2018.7.0
seo-title: Notas de versão de 2018.7.0
description: 'null'
seo-description: Siga esta página para obter informações sobre a versão 2018.7.0 do Gerenciador de nuvem.
uuid: d 7 b 49 e 32-01 dc -48 ce-b 744-e 6 a 806 fbdd 8 a
contentOwner: jsyal
topic-tags: notas-notas
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b 64 bf 9 ab -27 ed -4 f 33-adc 8-d 73 d 34094 f 1 b
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de versão de 2018.7.0 {#release-notes-for}

A seção a seguir descreve a versão [!UICONTROL Cloud Manager] 2018.7.0 que fornece o recurso *de rastreamento automático* .

**O rastreamento automático** é ativado através de escala horizontal de `Dispatcher/Publish` segmentos no ambiente de produção para suportar um aumento súbito de carga, volume, acesso e outras métricas monitoradas definidas.

## Data de lançamento {#release-date}

A Data de lançamento da [!UICONTROL Cloud Manager] versão 2018.7.0 é 10 de setembro de 20 18.

## Novidades {#what-s-new}

* **Provisionamento** - [!UICONTROL Cloud Manager] agora terá a capacidade de fazer o controle automático do ambiente de produção no programa do cliente, dimensionando horizontalmente com os segmentos do Dispatcher/Publish. Novo na interface do usuário é a seção Provisionamento na Configuração de programa que será exibida se a definição de metas automática estiver ativada no programa do cliente. Consulte [Configuração do programa](setting-up-program.md) para saber mais.

* **Ambientes** - agora é possível visualizar uma exibição detalhada dos ambientes de Produção e Stage juntamente com o tamanho, armazenamento, região e status dos nós associados a cada ambiente. Consulte [Gerenciar seus ambientes](manage-your-environment.md) para saber mais.

* **Análise de qualidade de código** - Nova regra para identificar o uso incorreto da API. Consulte Regras de qualidade de código [personalizadas](custom-code-quality-rules.md) para saber mais.

* **Teste de desempenho** - enquanto exibe resultados de teste de desempenho, os gráficos para Uso da CPU, Disco de uso de CPU e Tempo de espera de disco, Taxa de erro de página, Uso de largura de banda do disco, Uso de largura de banda de rede, Tempo de resposta da página máxima e Tempo de resposta da página Percent5 ª percentil estão disponíveis. Consulte * seção Teste de desempenho * em [Entender a página de Resultados](understand-your-test-results.md) de teste.

* **Teste de desempenho** - ao visualizar resultados de teste de desempenho, a lista de erros de página e solicitações lentas pode ser baixada. Consulte * seção Teste de desempenho * em [Entender a página de Resultados](understand-your-test-results.md) de teste.

## Correções de erros {#bug-fixes}

* Em determinadas circunstâncias, a sincronização interna do sistema falhou de forma inadequada, resultando em exibições inconsistentes de dados.
* Em alguns casos, o acionador do pipeline manual não era selecionado automaticamente levando a problemas de validação de formulário.
* Scripts de criação de clientes específicos podem causar falhas durante a etapa de compilação com base nas incompatibilidades do plug-in.

## Problemas conhecidos {#known-issues}

* Embora os clientes possam selecionar o acionador de commit, o pipeline pode não iniciar realmente com base em novos comandos.
* A barra lateral [!UICONTROL Experience Cloud] de notificação pode não carregar notificações consistentemente. No entanto, as notificações estão visíveis no [!UICONTROL Experience Cloud] e, se configuradas, ainda serão enviadas por email.

