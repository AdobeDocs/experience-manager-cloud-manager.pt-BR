---
title: Notas de versão de 2019.7.0
seo-title: Notas de versão do Gerenciador do AEM Cloud para 2019.7.0
description: Siga esta página para obter informações sobre a versão 2019.7.0 do Gerenciador de nuvem.
seo-description: Siga esta página para obter informações sobre a versão 2019.7.0 do Gerenciador de AEM Cloud.
translation-type: tm+mt
source-git-commit: 7cfa0cf66efd5891263bfcc83a5149daec5c8b67

---

# Release Notes for 2019.7.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.7.0 Release adds new code quality rules and new Product Update wizard. Siga as seções abaixo para obter mais detalhes.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.7.0 is July 18, 2019 .

## Novidades {#whats-new}

Agora há uma notificação da Experience Cloud enviada no início de uma implantação de produção.

## Bug Fixes {#bug-fixes}

* Em alguns casos, o Experience D Manager executaria a análise de código estática nos arquivos Python e PHP.
* Os pacotes que continham o filevault installhooks não eram executados de forma consistente na etapa de qualidade do código.
* Em determinadas combinações, problemas de qualidade de código não eram classificados de forma consistente.
* Há alguns problemas visuais na página de execução do pipeline.
* A etapa de teste de desempenho pode falhar aleatoriamente, devido a restrições de recursos da infraestrutura subjacente da nuvem.
* Algumas compilações do cliente falhavam devido a problemas de rede.