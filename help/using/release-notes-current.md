---
title: Notas de versão para 2020.7.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.7.0
description: Siga esta página para obter informações sobre a versão 2020.7.0 do Cloud Manager
seo-description: Siga esta página para obter informações sobre a versão 2020.7.0 do AEM Cloud Manager
translation-type: tm+mt
source-git-commit: a4ea83c0b64515915871956c1cd3e53606f1c26b
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 7%

---

# Notas de versão para 2020.7.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2020.7.0.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2020.7.0 é 9 de julho de 2020.

## Novidades {#whats-new}

* A detecção e anexação de instâncias do dispatcher de balanceadores de carga durante implantações de produção agora funciona de forma mais consistente.

* O container de criação do Cloud Manager agora é compatível com Java 8 e Java 11.

## Correções de erros {#bug-fixes}

* As opções **Cancelar** e **Salvar** na página Edição de Pipeline de Não Produção nem sempre estavam visíveis.

* Certas falhas no processo de qualidade do código podem resultar na não geração correta do arquivo de log.

* Alguns grandes logs de etapas de pipeline não puderam ser baixados consistentemente pela interface do usuário.

## Problemas conhecidos {#known-issues}

* Quando um ambiente AMS contém uma instância stand-by, a mensagem registrada informa que a instância está inativa em vez de no modo de espera.

* Devido a uma mudança na forma como a cobertura de código é calculada, a versão _mínima_ do plug-in Jacoco agora é 0.7.5.201505241946 (lançado em maio de 2015). Os clientes que referenciarem explicitamente uma versão mais antiga receberão uma mensagem de erro no processo de qualidade do código.
