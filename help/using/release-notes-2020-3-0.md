---
title: Notas da versão 2020.3.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.3.0
description: Siga esta página para obter informações sobre a versão 2020.3.0 do Cloud Manager
seo-description: Siga esta página para obter informações sobre a versão 2020.3.0 do AEM Cloud Manager
translation-type: tm+mt
source-git-commit: e7da473a22bec1d3d9b3d39bf654af0c596fe86d
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 51%

---

# Notas da versão 2020.3.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2020.3.0.

## Data de lançamento {#release-date}

A data de lançamento da versão 2020.3.0 [!UICONTROL Cloud Manager] é 5 de março de 2020.

## Novidades {#whats-new}

* O registro da etapa de build já está disponível, enquanto a etapa de build está em execução.
* Algumas das mensagens na página de detalhes de execução do pipeline foram editadas para maior clareza.

## Correções de erros {#bug-fixes}

* Determinadas configurações de implantação podem fazer com que os registros das etapas de implantação fiquem indisponíveis se a implantação falhar.
* Falhas específicas nas etapas de implantação para programas Managed Services podem causar falha no start das execuções subsequentes.
* Ocasionalmente, ocorria uma falha na instância efêmera SonarQube usada na etapa de build, ao iniciar dentro do tempo limite configurado.
* Em projetos específicos, os objetos *ResourceResolver devem ser sempre fechados*, gerando uma Exceção de Null Pointer. No entanto, isso não teve impacto na execução do pipeline.