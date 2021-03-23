---
title: Notas da versão 2019.9.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.9.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2019.9.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2019.9.0.
feature: Informações da versão
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 5%

---

# Notas da versão 2019.9.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.9.0 atualiza os critérios do teste de segurança, adiciona gráficos de monitoramento disponíveis para download e corrige alguns problemas de usabilidade relatados pelo cliente.

## Data de lançamento {#release-date}

A data de lançamento da versão [!UICONTROL Cloud Manager] 2019.9.0 é 12 de setembro de 2019.

## Novidades {#whats-new}

* A categorização da verificação de integridade do Filtro do Referenciador do Sling foi alterada de Crítico para Importante.
* A categorização da verificação de integridade da Configuração do Gerenciador de Biblioteca HTML foi alterada de Crítico para Importante.
* Os gráficos de monitoramento agora podem ser baixados. Consulte [Monitorar os ambientes](monitor-your-environments.md) para obter mais detalhes.
* Se um programa não tiver um ambiente de AEM de produção, clicar no cartão do programa na página de aterrissagem navegará até a página de visão geral do Cloud Manager, não produzirá uma caixa de diálogo de erro.
* O cartão **Pipeline Settings** na página **Overview** foi redenominado **Production Pipeline Settings**.
* Os botões de opção Important Failure Behavior foram removidos dos pipelines de qualidade de código somente.
* A página **Activity** agora exibe o nome do pipeline para cada execução.
* A página de execução agora exibe o nome do pipeline.
* A caixa de diálogo Resumo da qualidade do código agora mostra uma descrição para cada classificação.

## Correções de erros {#bug-fixes}

* Alguns usuários não conseguiam visualizar detalhes de execução enquanto aguardavam aprovação.
* Na página **Visão geral**, a margem direita não era consistente.
* O contêiner de criação pode ficar sem memória em projetos grandes.
* Em determinadas circunstâncias, a regra BannedPaths OakPAL não identificou o conteúdo instalado em /libs.
* Quando uma porta de qualidade foi rejeitada, o cabeçalho da caixa de diálogo ainda exibia *Parcialmente Aprovado*.

## Problemas conhecidos {#known-issues}

* O download de gráficos de monitoramento não está disponível no Safari.
