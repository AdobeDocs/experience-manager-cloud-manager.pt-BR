---
title: Notas de versão para 2019.8.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.8.0
description: Siga esta página para obter informações sobre a versão 2019.8.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2019.8.0 do AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: c07e88564dc1419bd0305c9d25173a8e0e1f47cf
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 5%

---

# Notas de versão para 2019.8.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.8.0 adiciona suporte para pacotes de conteúdo criados seletivamente, melhora o desempenho da compilação e corrige uma variedade de bugs secundários.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2019.8.0 é 19 de agosto de 2019.

## Novidades {#whats-new}

* Nova interface de linha de comando para a API do Gerenciador de nuvem, capacitada pela CLI [de E/S da](https://github.com/adobe/aio-cli-plugin-cloudmanager)Adobe.
* Os pacotes de conteúdo específico produzidos pela compilação podem ser declarados como ignoráveis e não serão implantados. Consulte ***Ignorando pacotes*** de conteúdo na seção [Criar um projeto](/help/using/create-an-application-project.md) de aplicativo AEM para obter mais detalhes.
* O conjunto de dependências pré-carregadas no container build foi retrabalhado para evitar algumas solicitações de rede desnecessárias.
* A mensagem na página de visão geral de determinados programas configurados incorretamente foi aprimorada.

## Correções de erros {#bug-fixes}

* Ao acessar os relatórios de SLA, o ano padrão era 2018, não 2019.
* Para nomes de ambientes longos, o seletor de ambientes na tela Relatórios não aumentou corretamente o tamanho.
* A regra de qualidade de código ***ConfigAndInstallshouldOnlyContainOsgiNodes*** produziu falsos positivos quando o componente Sling Rewriter foi usado.
* A regra de qualidade de código ***ConfigAndInstallshouldOnlyContainOsgiNodes*** produziu falsos positivos para determinadas estruturas de caminho incomuns.
* Clientes somente de ativos podem não ter sido consistentemente capazes de navegar para seus ambientes AEM.
* A caixa de diálogo Criar uma Ramificação e um Projeto foi renderizada de forma diferente em navegadores diferentes.
