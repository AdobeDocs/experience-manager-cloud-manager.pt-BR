---
title: Notas de versão para 2019.7.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.7.0
description: Siga esta página para obter informações sobre a versão 2019.7.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2019.7.0 do AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5

---

# Notas de versão para 2019.7.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.7.0 adiciona atualizações às notificações e melhorias da Experience Cloud como correções de erros. Siga as seções abaixo para obter mais detalhes.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2019.7.0 é 18 de julho de 2019.

## Novidades {#whats-new}

Agora há uma notificação da Experience Cloud enviada no início de uma implantação de produção.

## Correções de erros {#bug-fixes}

* Em alguns casos, o Cloud Manager executaria a análise de código estático em arquivos Python e PHP.
* Os pacotes que continham FileVault InstallHooks não eram executados consistentemente na etapa de qualidade do código.
* Em determinadas combinações, os problemas de qualidade de código não foram classificados de forma consistente.
* Houve alguns problemas visuais na página de execução do pipeline.
* A etapa de teste de desempenho pode falhar aleatoriamente às vezes devido a restrições de recursos da infraestrutura de nuvem subjacente.
* Certas compilações de clientes falhariam devido a problemas de rede.