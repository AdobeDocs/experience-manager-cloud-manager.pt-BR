---
title: Notas da versão 2019.6.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.6.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2019.6.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2019.6.0.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 9%

---

# Notas da versão 2019.6.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.6.0 adiciona novas regras de qualidade de código e o novo assistente de Atualização de produto. Siga as seções abaixo para obter mais detalhes.

## Data de lançamento {#release-date}

A data de lançamento da versão de [!UICONTROL Cloud Manager] 2019.6.0 é 20 de junho de 2019 .

## Novidades {#whats-new}

* Novo assistente de atualização de produto para ajudar os clientes a executar uma atualização de AEM com êxito. Consulte [Assistente de atualização do produto](overview-productupdate-wizard.md) para saber mais.
* Regras de qualidade do código que examinam as estruturas de conteúdo. Consulte [Regras de qualidade do código personalizado](custom-code-quality-rules.md) para obter mais informações.
* O tamanho máximo de um push de git foi aumentado para 1 GB.

## Correções de erros {#bug-fixes}

* Em alguns casos, os pipelines não puderam ser iniciados devido a uma falha anterior.

## Problemas conhecidos {#known-issues}

* O download CSV de qualidade do código nem sempre é classificado de acordo com a gravidade.
* Falsos positivos podem ser relatados pela regra *ConfigAndInstallshouldOnlyContainOsgiNodes* se as configurações OSGi forem colocadas em uma pasta aninhada em uma pasta *config*.