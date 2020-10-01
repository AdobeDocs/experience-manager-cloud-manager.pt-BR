---
title: Notas da versão 2020.10.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.10.0
description: Siga esta página para obter informações sobre a versão 2020.10.0 do Cloud Manager
seo-description: Siga esta página para obter informações sobre a versão 2020.10.0 do AEM Cloud Manager
translation-type: tm+mt
source-git-commit: aad2da58e5934999884553619dd97d42cc725d88
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 9%

---

# Notas da versão 2020.10.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] versão 2020.10.0.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2020.10.0 é 1 de outubro de 2020.

## Correções de erros {#bug-fixes}

* O rastreador usado para teste de desempenho considerava incorretamente certos tipos de recursos como links da Web válidos.

* Em algumas situações, a etapa de conclusão no teste de desempenho não foi corretamente manipulada, resultando em etapas de longa duração.

* Quando a invalidação do cache do dispatcher era configurada para implantações de produção, a invalidação às vezes era executada duas vezes.