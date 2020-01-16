---
title: Notas de versão para 2019.12.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.12.0
description: Siga esta página para obter informações sobre a versão 2019.12.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2019.12.0 do AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: a96500b57c980d31d3a70341d8be7b92ae73a1c5

---

# Notas de versão para 2019.12.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] versão 2019.12.0 e adiciona atualizações à execução de pipeline e melhorias nas verificações de qualidade de código.
Siga as seções abaixo para obter mais detalhes.

## Release Date {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2019.12.0 é 12 de dezembro de 2019.

## Novidades {#whats-new}

* As etapas na execução do pipeline agora mostram o carimbo de data e hora de conclusão para cada etapa.
* As verificações de qualidade de código para projetos que não contêm código Java agora reportam uma taxa de cobertura de código de 100%.
* A verificação de integridade da Configuração do Dispatcher CQ foi removida.


## Correções de erros {#bug-fixes}

* As datas não eram exibidas corretamente em determinados navegadores.
* Em casos raros, o pipeline de produção passaria para a etapa de aprovação enquanto o teste de desempenho ainda estava em execução.
* Em determinados estados, os botões na área superior da página de visão geral não estavam alinhados corretamente.
* Em determinadas circunstâncias, os utilizadores não autorizados viram um botão para iniciar o pipeline, embora o botão em si não fosse clicável.
* Os botões de ação para pipelines de não produção às vezes eram exibidos no local errado.
* Os pacotes com o tipo de nó granite:Ranking não puderam ser verificados para verificar se havia certas violações de regras de qualidade.
* Algumas falhas no processo de qualidade do código foram contadas incorretamente como erros.
* Não foi possível carregar os dados de monitoramento para determinadas topologias.
