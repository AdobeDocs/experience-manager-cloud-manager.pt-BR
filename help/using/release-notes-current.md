---
title: Notas de versão de 2019.9.0
seo-title: Notas de versão do Gerenciador do AEM Cloud para 2019.9.0
description: Siga esta página para obter informações sobre a versão 2019.9.0 do Gerenciador de nuvem.
seo-description: Siga esta página para obter informações sobre a versão 2019.9.0 do Gerenciador de AEM Cloud.
translation-type: tm+mt
source-git-commit: 26014cfabfee6226033ba2fc1167d8f5509e17c6

---

# Notas de versão de 2019.9.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.9.0 atualiza os critérios de teste de segurança, adiciona gráficos de monitoramento que podem ser obtidos por download e corrigem alguns problemas de usabilidade relatados pelo cliente.

## Data de lançamento {#release-date}

A Data de lançamento da [!UICONTROL Cloud Manager] versão 2019.9.0 é 12 de setembro de 22 19.

## Novidades {#whats-new}

* A categorização da verificação de integridade do Filtro de referência foi alterada de Fundamental para importante.
* A categorização da verificação de integridade de Configuração do Gerenciador de biblioteca HTML foi alterada de Fundamental para importante.
* Agora, os gráficos de monitoramento podem ser baixados. Consulte [Monitorar seus ambientes](monitor-your-environments.md) para obter mais detalhes.
* Se um programa não tiver um ambiente AEM de produção, clicar no cartão de programas da página de aterrissagem navegará até a página de visão geral do Gerenciador de nuvem, e não produz uma caixa de diálogo de erro.
* O **Cartão de configurações** do pipeline na página **Visão geral** foi retornado para **Configurações do Pipeline de produção**.
* Os botões de opção Importante Comportamento de falha foram removidos de pipeline somente de qualidade de código.
* A página **Atividade** agora exibe o nome do pipeline para cada execução.
* A página de execução agora exibe o nome do pipeline.
* A caixa de diálogo de resumo de qualidade de código agora mostra uma descrição para cada classificação.

## Correções de erros {#bug-fixes}

* Alguns usuários não puderam visualizar os detalhes da execução quando estava aguardando aprovação.
* Na **página Visão geral** , a margem direita não era consistente.
* O contêiner de compilação pode ficar sem memória em grandes projetos.
* Em determinadas circunstâncias, a regra bannedpaths oakpal não identificava o conteúdo instalado em /libs.
* Quando um portfólio de qualidade foi rejeitado, o cabeçalho da caixa de diálogo ainda mostrava *parcialmente aprovado*.

## Problemas conhecidos {#known-issues}

* O download de gráficos de monitoramento não está disponível no Safari.
