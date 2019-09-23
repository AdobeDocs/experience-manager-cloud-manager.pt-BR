---
title: Notas de versão para 2018.9.0
seo-title: Notas de versão do AEM Cloud Manager para 2018.8.0
description: Siga esta página para obter informações sobre a versão 2018.9.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2018.9.0 do AEM Cloud Manager.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas de versão
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: 949d3cf0239a02875ba4ad1888e081f104dec2e2

---


# Notas de versão para 2018.9.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2018.9.0 adiciona suporte para uma API baseada em E/S da Adobe, incluindo Eventos, para integração do pipeline CI/CD [!UICONTROL Cloud Manager]da Adobe com outros sistemas. Ele também inicia a regravação da camada da interface no React.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2018.9.0 é 1 de novembro de 2018.

## Novidades {#whats-new}

* **Pipeline** CI/CD - Nova API e sistema de evento para integrar o pipeline CI/CD [!UICONTROL Cloud Manager]do sistema com outros sistemas. Consulte a Documentação da [!UICONTROL Cloud Manager] API (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) para obter mais informações.

* **Interface do usuário** - Introdução à nova camada da interface do usuário que é mais ágil e mais eficiente.

## Correções de erros {#bug-fixes}

* Em [!UICONTROL Cloud Manager] 2018.8.0, as durações da página Atividade eram listadas em minutos e horas, mas essas informações não eram refletidas no cabeçalho da tabela.
* Em raras ocasiões, os clientes não conseguiam iniciar o assistente de novos projetos de aplicativos.
* O rótulo do botão na caixa de diálogo do assistente para novo projeto de aplicativo estava enganoso.
* Em algumas circunstâncias, clicar no botão Detalhes na página Atividade redirecionaria para a página Visão geral.
* Algumas circunstâncias raras e inesperadas resultaram em um cartão ausente na página Visão geral.
* O ícone Ativos era exibido na página Lista de programas para todos os clientes.
* Quando havia falhas de back-end, às vezes uma execução de pipeline parecia permanecer na etapa *Validate* .
* Em determinadas circunstâncias, a duração da descrição do programa foi mal calculada.

## Problemas conhecidos {#known-issues}

* As ramificações criadas usando o Assistente de projeto de aplicativo não podem conter traços.
* A barra lateral de notificações da Adobe [!UICONTROL Experience Cloud] pode não carregar as notificações de forma consistente. No entanto, as notificações estão visíveis na Adobe [!UICONTROL Experience Cloud] e, se configuradas, ainda serão enviadas por email.

