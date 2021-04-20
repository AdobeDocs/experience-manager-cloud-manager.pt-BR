---
title: Notas da versão 2019.12.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.12.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2019.12.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2019.12.0.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 6%

---


# Notas da versão 2019.12.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2019.12.0 e adiciona atualizações à execução do pipeline e melhorias para verificações de qualidade de código.
Siga as seções abaixo para obter mais detalhes.

## Data de lançamento {#release-date}

A data de lançamento da versão [!UICONTROL Cloud Manager] 2019.12.0 é 12 de dezembro de 2019.

## Novidades {#whats-new}

* As etapas na execução do pipeline agora mostram o carimbo de data e hora de conclusão para cada etapa.
* As verificações de qualidade de código para projetos que não contêm código Java agora relatam uma taxa de cobertura de código de 100%.
* A verificação de integridade da Configuração do Dispatcher CQ foi removida.

## Correções de erros {#bug-fixes}

* As datas não eram exibidas corretamente em determinados navegadores.
* Em casos raros, o pipeline de produção mudaria para a etapa de aprovação enquanto o teste de desempenho ainda estava em execução.
* Em determinados estados, os botões na área superior da página de visão geral não eram alinhados corretamente.
* Em determinadas circunstâncias, usuários não autorizados viram um botão para iniciar o pipeline, embora o botão em si não fosse clicável.
* Os botões de ação para pipelines que não sejam de produção às vezes eram exibidos no local errado.
* Os pacotes com o tipo de nó granite:Ranking não puderam ser examinados em busca de determinadas violações de regras de qualidade.
* Certas falhas no processo de qualidade do código foram contadas incorretamente como erros.
* Não foi possível carregar dados de monitoramento para determinadas topologias.
