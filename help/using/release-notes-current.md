---
title: Notas de versão de 2019.6.0
seo-title: Notas de versão do Gerenciador do AEM Cloud para 2019.6.0
description: Siga esta página para obter informações sobre a versão 2019.6.0 do Gerenciador de nuvem.
seo-description: Siga esta página para obter informações sobre a versão 2019.6.0 do Gerenciador de AEM Cloud.
translation-type: tm+mt
source-git-commit: 7373f674b9804c83fad0871a74ef85280ea24962

---

# Release Notes for 2019.6.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.6.0 Release adds new code quality rules and new Product Update wizard. Siga as seções abaixo para obter mais detalhes.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.6.0 is June 20, 2019 .

## Novidades {#whats-new}

* Novo assistente de atualização de produto para ajudar os clientes a executar uma atualização do AEM com êxito. Refer to [Product Update Wizard](overview-productupdate-wizard.md) to learn more.
* Regras de qualidade do código que examinam as estruturas de conteúdo. Refer to [Custom Code Quality Rules](custom-code-quality-rules.md) for more information.
* O tamanho máximo de um push git aumentou para 1 GB.

## Bug Fixes {#bug-fixes}

* Em alguns casos, os pipeline não puderam ser iniciados devido a uma falha anterior.

## Problemas conhecidos {#known-issues}

* O download CSV de qualidade de código nem sempre é classificado de acordo com a gravidade.
* False positives may be reported by the *ConfigAndInstallShouldOnlyContainOsgiNodes* rule if OSGi configurations are placed in a nested folder under a *config* folder.
