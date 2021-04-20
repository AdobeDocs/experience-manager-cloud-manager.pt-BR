---
title: Notas da versão 2019.8.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.8.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2019.8.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2019.8.0.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 8%

---

# Notas da versão 2019.8.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.8.0 adiciona suporte para pacotes de conteúdo construído seletivos, melhora o desempenho da compilação e corrige uma variedade de pequenos erros.

## Data de lançamento {#release-date}

A Data de lançamento da versão [!UICONTROL Cloud Manager] 2019.8.0 é 19 de agosto de 2019.

## Novidades {#whats-new}

* Nova interface de linha de comando para a API do Cloud Manager, fornecida pelo [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* Pacotes de conteúdo específicos produzidos pela build podem ser declarados como ignorados e não serão implantados. Consulte [Ignorando pacotes de conteúdo](/help/using/setting-up-project.md#skipping-content-packages) para obter mais detalhes.
* O conjunto de dependências pré-carregadas no contêiner de criação foi retrabalhado para evitar algumas solicitações desnecessárias de rede.
* A mensagem na página de visão geral de determinados programas configurados incorretamente foi aprimorada.

## Correções de erros {#bug-fixes}

* Ao acessar os relatórios do SLA, o ano padrão era 2018, não 2019.
* Para nomes de ambiente longos, o seletor de ambiente na tela Relatórios não aumentou corretamente no tamanho.
* A regra de qualidade de código ***ConfigAndInstallshouldOnlyContainOsgiNodes*** produziu falsos positivos quando o componente do Sling Rewriter foi usado.
* A regra de qualidade de código ***ConfigAndInstallshouldOnlyContainOsgiNodes*** produziu falsos positivos para determinadas estruturas de caminho incomuns.
* Clientes somente de ativos podem não ter navegado de forma consistente para seus ambientes de AEM.
* A caixa de diálogo Criar uma ramificação e projeto foi renderizada de forma diferente em navegadores diferentes.
