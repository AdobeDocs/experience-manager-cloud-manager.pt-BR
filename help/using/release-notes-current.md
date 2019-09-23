---
title: Notas de versão para 2019.9.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.9.0
description: Siga esta página para obter informações sobre a versão 2019.9.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2019.9.0 do AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 26014cfabfee6226033ba2fc1167d8f5509e17c6

---

# Notas de versão para 2019.9.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.9.0 atualiza os critérios de teste de segurança, adiciona gráficos de monitoramento disponíveis para download e corrige alguns problemas de usabilidade relatados pelo cliente.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2019.9.0 é 12 de setembro de 2019.

## Novidades {#whats-new}

* A categorização da verificação de integridade do Filtro do Referenciador de Sling foi alterada de Crítico para Importante.
* A categorização da verificação de integridade da configuração do HTML Library Manager foi alterada de Crítico para Importante.
* Os gráficos de monitoramento agora podem ser baixados. Consulte [Monitorar seus ambientes](monitor-your-environments.md) para obter mais detalhes.
* Se um programa não tiver um ambiente AEM de produção, clicar no cartão do programa na página de aterrissagem navegará até a página de visão geral do Gerenciador de nuvem e não gerará uma caixa de diálogo de erro.
* O cartão de configurações **do** pipeline na página **Visão geral** foi chamado de Configurações **do pipeline de** produção.
* Os botões de opção Important Failure Behavior (Comportamento de falha importante) foram removidos de pipelines somente com qualidade de código.
* A página **Atividade** agora exibe o nome do pipeline para cada execução.
* A página de execução agora exibe o nome do pipeline.
* A caixa de diálogo de resumo Qualidade do código agora mostra uma descrição para cada classificação.

## Correções de erros {#bug-fixes}

* Alguns usuários não conseguiam visualizar os detalhes de uma execução enquanto aguardavam aprovação.
* Na página **Visão geral** , a margem direita não era consistente.
* O contêiner de compilação pode ficar sem memória em projetos grandes.
* Em determinadas circunstâncias, a regra BannedPaths OakPAL não identificou o conteúdo instalado em /libs.
* Quando uma porta de qualidade foi rejeitada, o cabeçalho da caixa de diálogo ainda mostrava *Parcialmente Aprovado*.

## Problemas conhecidos {#known-issues}

* O download de gráficos de monitoramento não está disponível no Safari.
