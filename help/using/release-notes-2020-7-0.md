---
title: Notas da versão 2020.7.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.7.0
description: Siga esta página para obter informações sobre a versão 2020.7.0 do Cloud Manager
seo-description: Siga esta página para obter informações sobre a versão 2020.7.0 do AEM Cloud Manager
translation-type: tm+mt
source-git-commit: c35398110e9d8311bf58f217efdd082cf0cfd90a
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 51%

---

# Notas da versão 2020.7.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2020.7.0.

## Data de lançamento {#release-date}

A data de lançamento da versão 2020.7.0 [!UICONTROL Cloud Manager] é 9 de julho de 2020.

## Novidades {#whats-new}

* A detecção e anexação de instâncias do dispatcher de balanceadores de carga durante implantações de produção agora funciona de forma mais consistente.

* O container de build do Cloud Manager agora é compatível com Java 8 e Java 11.

* Os pipelines do Cloud Manager agora oferecem suporte a variáveis e segredos definidos pelo cliente.
Consulte [Variáveis de pipeline](/help/using/build-environment-details.md#pipeline-variables) para saber mais.

## Correções de erros {#bug-fixes}

* As opções **Cancelar** e **Salvar** na página Edição de Pipeline de Não Produção nem sempre estavam visíveis.

* Certas falhas no processo de qualidade do código podiam resultar na geração incorreta do arquivo de log.

* Grandes logs de etapas de pipeline não podiam ser baixados consistentemente pela interface do usuário.

## Problemas conhecidos {#known-issues}

* Quando um ambiente AMS contém uma instância stand-by, a mensagem registrada informa que a instância está inativa em vez de no modo de espera.

* Devido a uma mudança na forma como a cobertura de código é calculada, a versão _mínima_ do plug-in Jacoco agora é a 0.7.5.201505241946 (lançada em maio de 2015). Os clientes que indicarem uma versão mais antiga receberão uma mensagem de erro no processo de qualidade do código.
