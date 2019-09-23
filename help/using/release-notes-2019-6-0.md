---
title: Notas de versão para 2019.6.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.6.0
description: Siga esta página para obter informações sobre a versão 2019.6.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2019.6.0 do AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 7cfa0cf66efd5891263bfcc83a5149daec5c8b67

---

# Notas de versão para 2019.6.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.6.0 adiciona novas regras de qualidade de código e o novo assistente de atualização de produto. Siga as seções abaixo para obter mais detalhes.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2019.6.0 é 20 de junho de 2019.

## Novidades {#whats-new}

* Novo Assistente de atualização de produto para ajudar os clientes a executar com êxito uma atualização do AEM. Consulte o Assistente [de atualização de](overview-productupdate-wizard.md) produto para saber mais.
* Regras de qualidade de código que examinam estruturas de conteúdo. Consulte Regras [de qualidade de código](custom-code-quality-rules.md) personalizado para obter mais informações.
* O tamanho máximo de um push de git foi aumentado para 1 GB.

## Correções de erros {#bug-fixes}

* Em alguns casos, os gasodutos não puderam ser iniciados devido a uma falha anterior.

## Problemas conhecidos {#known-issues}

* O download CSV de qualidade de código nem sempre é classificado de acordo com a gravidade.
* Os falsos positivos podem ser relatados pela regra *ConfigAndInstallshouldOnlyContainOsgiNodes* se as configurações OSGi forem colocadas em uma pasta aninhada em uma pasta *de configuração* .