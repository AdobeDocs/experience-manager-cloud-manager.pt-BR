---
title: Notas de versão para 2020.3.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.3.0
description: Siga esta página para obter informações sobre a versão 2020.3.0 do Cloud Manager
seo-description: Siga esta página para obter informações sobre a versão 2020.3.0 do AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 44671d89edad0ccb6ded998b62beb5fa012678e9

---

# Notas de versão para 2020.3.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2020.3.0.

## Release Date {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2020.3.0 é 5 de março de 2020.

## Novidades {#whats-new}

* O log da etapa de compilação agora está disponível enquanto a etapa de compilação está em execução.
* Algumas mensagens na página de detalhes de execução do pipeline foram editadas para maior clareza.

## Correções de erros {#bug-fixes}

* Determinadas configurações de implantação podem fazer com que os registros das etapas de implantação fiquem indisponíveis se a implantação falhar.
* Falhas específicas nas etapas de implantação para programas de Serviços gerenciados podem causar falha ao iniciar execuções subsequentes.
* A instância efêmera SonarQube usada na etapa de compilação falhou ocasionalmente ao iniciar dentro do tempo limite configurado.
* Em projetos específicos, os objetos *ResourceResolver devem ser sempre fechados* , gerando uma Exceção de Ponteiro Nulo; no entanto, tal não teve impacto na execução do gasoduto.


