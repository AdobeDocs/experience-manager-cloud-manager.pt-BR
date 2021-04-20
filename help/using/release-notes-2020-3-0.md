---
title: Notas da versão 2020.3.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.3.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2020.3.0
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2020.3.0
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 51%

---

# Notas da versão 2020.3.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2020.3.0.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2020.3.0 é 5 de março de 2020.[!UICONTROL Cloud Manager]

## Novidades {#whats-new}

* O registro da etapa de build já está disponível, enquanto a etapa de build está em execução.
* Algumas das mensagens na página de detalhes de execução do pipeline foram editadas para maior clareza.

## Correções de erros {#bug-fixes}

* Certas configurações de implantação podem fazer com que os logs das etapas de implantação fiquem indisponíveis se a implantação falhar.
* Falhas específicas nas etapas de implantação para programas Managed Services podem causar falha no início das execuções subsequentes.
* Ocasionalmente, ocorria uma falha na instância efêmera SonarQube usada na etapa de build, ao iniciar dentro do tempo limite configurado.
* Em projetos específicos, os objetos *ResourceResolver devem ser sempre fechados*, gerando uma Exceção de Null Pointer. No entanto, isso não teve impacto na execução do pipeline.