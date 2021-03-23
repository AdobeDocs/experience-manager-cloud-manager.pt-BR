---
title: Notas da versão 2018.9.0
seo-title: Notas de versão do AEM Cloud Manager para 2018.9.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2018.9.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2018.9.0.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: Informações da versão
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 9%

---


# Notas da versão 2018.9.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2018.9.0 adiciona suporte para uma API baseada em Adobe I/O, incluindo Eventos, para integrar o pipeline de CI/CD de [!UICONTROL Cloud Manager] com outros sistemas. Ele também inicia a regravação da camada da interface no React.

## Data de lançamento {#release-date}

A Data de lançamento da versão [!UICONTROL Cloud Manager] 2018.9.0 é 1 de novembro de 2018.

## Novidades {#whats-new}

* **Pipeline de CI/CD**  - Nova API e sistema de evento para integrar o pipeline de CI/CD  [!UICONTROL Cloud Manager]de outros sistemas. Consulte a [!UICONTROL Cloud Manager] Documentação da API (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) para obter mais informações.

* **Interface do usuário**  - Introdução de uma nova camada de interface do usuário que é mais responsiva.

## Correções de erros {#bug-fixes}

* Em [!UICONTROL Cloud Manager] 2018.8.0, as durações da página Atividade foram listadas em minutos e horas, mas essas informações não foram refletidas no cabeçalho da tabela.
* Em raras ocasiões, os clientes não conseguiram iniciar o assistente do novo projeto de aplicativo.
* O rótulo do botão na caixa de diálogo do assistente do novo projeto de aplicativo era enganoso.
* Em algumas circunstâncias, clicar no botão Detalhes na página Atividade redirecionaria para a página Visão geral .
* Algumas circunstâncias raras e inesperadas resultaram em um cartão ausente na página Visão geral .
* O ícone Ativos era exibido na página Lista de programas para todos os clientes.
* Quando havia falhas de back-end, às vezes uma execução de pipeline parecia permanecer na etapa *Validate*.
* Em determinadas circunstâncias, a duração da descrição do programa foi mal calculada.

## Problemas conhecidos {#known-issues}

* As ramificações criadas usando o Assistente de Projeto do Aplicativo não podem conter traços.
* A barra lateral de notificação Adobe [!UICONTROL Experience Cloud] pode não carregar as notificações de maneira consistente. No entanto, as notificações estão visíveis no Adobe [!UICONTROL Experience Cloud] e, se configuradas, ainda serão enviadas por email.

