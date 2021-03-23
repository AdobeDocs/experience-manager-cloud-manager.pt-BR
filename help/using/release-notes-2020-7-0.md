---
title: Notas da versão 2020.7.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.7.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2020.7.0
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2020.7.0
feature: Informações da versão
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 52%

---

# Notas da versão 2020.7.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2020.7.0.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2020.7.0 é 9 de julho de 2020.[!UICONTROL Cloud Manager]

## Novidades {#whats-new}

* Desanexar e anexar instâncias do dispatcher dos balanceadores de carga durante implantações de produção agora funciona de forma mais consistente.

* O container de build do Cloud Manager agora é compatível com Java 8 e Java 11.

* Os pipelines do Cloud Manager agora oferecem suporte a variáveis e segredos definidos pelo cliente.
Consulte [Variáveis de pipeline](/help/using/build-environment-details.md#pipeline-variables) para saber mais.

## Correções de erros {#bug-fixes}

* As opções **Cancelar** e **Salvar** na página Editar pipeline de não produção nem sempre estavam visíveis.

* Certas falhas no processo de qualidade do código podiam resultar na geração incorreta do arquivo de log.

* Grandes logs de etapas de pipeline não podiam ser baixados consistentemente pela interface do usuário.

## Problemas conhecidos {#known-issues}

* Quando um ambiente AMS contém uma instância de standby, a mensagem registrada declara que a instância está inativa, em vez de no modo de standby.

* Devido a uma mudança na forma como a cobertura de código é calculada, a versão _mínima_ do plug-in Jacoco agora é a 0.7.5.201505241946 (lançada em maio de 2015). Os clientes que indicarem uma versão mais antiga receberão uma mensagem de erro no processo de qualidade do código.
