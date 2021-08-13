---
title: Notas da versão 2020.1.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.1.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2020.1.0
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2020.1.0
feature: Informações da versão
exl-id: 105e526f-b3c6-49d2-bb4d-d19a5afad6cc
source-git-commit: f4b0957ce2dda55ad9b0d7a736263bece54d2139
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 9%

---

# Notas da versão 2020.1.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2020.1.0 e adiciona atualizações para acessar as credenciais do Git e a experiência de logon.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2020.1.0 é 16 de janeiro de 2020.[!UICONTROL Cloud Manager]

## Novidades {#whats-new}

* As credenciais do Git agora podem ser obtidas na interface do usuário do Cloud Manager. Consulte [Acesso ao Git](accessing-repos.md) para obter mais detalhes.
* A experiência de logon e a estrutura do URL foram alteradas como parte de uma iniciativa de todo o Adobe. Marcadores antigos serão redirecionados para os novos URLs.


## Correções de erros {#bug-fixes}

* As implantações em topologias somente para autor não implantaram alterações de configuração do dispatcher.
* Em determinadas configurações, não foi possível criar um pipeline somente de qualidade de código.
* O cartão de resumo do ambiente na página de visão geral às vezes não era renderizado corretamente.
* As execuções de pipeline podem atingir o tempo limite em topologias grandes.
