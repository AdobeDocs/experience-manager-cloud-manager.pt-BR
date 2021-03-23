---
title: Notas da versão 2020.10.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.10.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2020.10.0
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2020.10.0
feature: Informações da versão
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 11%

---

# Notas da versão 2020.10.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2020.10.0.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2020.10.0 é 1 de outubro de 2020.[!UICONTROL Cloud Manager]

## Correções de erros {#bug-fixes}

* O rastreador usado para teste de desempenho estava considerando incorretamente determinados tipos de recursos como links da Web válidos.

* Em algumas situações, a etapa de conclusão no teste de desempenho não foi manipulada corretamente, levando a etapas de longa duração.

* Quando a invalidação do cache do dispatcher foi configurada para implantações de produção, a invalidação às vezes foi executada duas vezes.