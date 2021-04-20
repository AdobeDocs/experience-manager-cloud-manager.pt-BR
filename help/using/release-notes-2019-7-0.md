---
title: Notas da versão 2019.7.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.7.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2019.7.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2019.7.0.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 8%

---

# Notas da versão 2019.7.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.7.0 adiciona atualizações às notificações e aprimoramentos do Experience Cloud como correções de erros. Siga as seções abaixo para obter mais detalhes.

## Data de lançamento {#release-date}

A data de lançamento da versão [!UICONTROL Cloud Manager] 2019.7.0 é 18 de julho de 2019.

## Novidades {#whats-new}

Agora há uma notificação Experience Cloud enviada no início de uma implantação de produção.

## Correções de erros {#bug-fixes}

* Em alguns casos, o Cloud Manager executaria a análise de código estático em arquivos Python e PHP.
* Os pacotes que continham FileVault InstallHooks não eram executados consistentemente na etapa de qualidade do código .
* Em determinadas combinações, os problemas de qualidade do código não eram classificados de forma consistente.
* Houve alguns problemas visuais na página de execução do pipeline.
* A etapa de teste de desempenho pode falhar aleatoriamente, às vezes, devido a restrições de recursos da infraestrutura de nuvem subjacente.
* Certas builds de clientes falhariam devido a problemas de rede.