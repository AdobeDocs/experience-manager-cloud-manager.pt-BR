---
title: Notas de versão de 2019.8.0
seo-title: Notas de versão do Gerenciador do AEM Cloud para 2019.8.0
description: Siga esta página para obter informações sobre a versão 2019.8.0 do Gerenciador de nuvem.
seo-description: Siga esta página para obter informações sobre a versão 2019.8.0 do Gerenciador de AEM Cloud.
translation-type: tm+mt
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5

---

# Notas de versão de 2019.8.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.8.0 adiciona suporte para pacotes de conteúdo construídos seletivos, melhora o desempenho da criação e corrige uma variedade de bugs menores.

## Data de lançamento {#release-date}

A Data de lançamento da [!UICONTROL Cloud Manager] versão 2019.8.0 é 19 de agosto de 29 19.

## Novidades {#whats-new}

* Nova interface de linha de comando à API do Gerenciador de nuvem, capacitada pelo CLI [da Adobe I/O](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* Os pacotes de conteúdo específicos produzidos pela criação podem ser declarados como ignoráveis e não serão implantados. Consulte ***a seção Ignorar pacotes*** de conteúdo em [Criar um projeto do aplicativo AEM](create-an-application-project.md) para obter mais detalhes.
* O conjunto de dependências pré-carregadas no contêiner de criação foi reformulado para evitar algumas solicitações de rede desnecessárias.
* A mensagem na página de visão geral de determinados programas configurados incorretamente foi aprimorada.

## Correções de erros {#bug-fixes}

* Ao acessar os relatórios SLA, o ano padrão era 2018, e não 2019.
* Para nomes de ambiente longos, o seletor de ambiente na tela Relatórios não aumentava adequadamente o tamanho.
* A regra de qualidade de código ***configandinstallbldonlycontainosginodes*** produziu falsos positivos quando o componente Sling Rewriter era usado.
* A regra de qualidade de código ***configandinstallbldonlycontainosginodes*** produziu falsos positivos para certas estruturas de caminho incomuns.
* Os clientes somente ativos podem não ter sido consistentemente capazes de navegar para seus ambientes AEM.
* A [!UICONTROL Create a Branch and Project] caixa de diálogo renderizada de forma diferente em navegadores diferentes.
