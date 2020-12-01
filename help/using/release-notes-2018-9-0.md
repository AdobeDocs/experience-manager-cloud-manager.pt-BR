---
title: Notas da versão 2018.9.0
seo-title: Notas de versão do AEM Cloud Manager para 2018.9.0
description: Siga esta página para obter informações sobre a versão 2018.9.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2018.9.0 do AEM Cloud Manager.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 5%

---


# Notas da versão 2018.9.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2018.9.0 adiciona suporte para uma API baseada em Adobe I/O, incluindo Eventos, para integrar o pipeline CI/CD de [!UICONTROL Cloud Manager] com outros sistemas. Ele também inicia a regravação da camada da interface no React.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2018.9.0 é 1 de novembro de 2018.

## Novidades {#whats-new}

* **Pipeline**  CI/CD - Nova API e sistema de Evento para integrar o pipeline CI/CD  [!UICONTROL Cloud Manager]do sistema com outros sistemas. Consulte [!UICONTROL Cloud Manager] Documentação da API (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) para obter mais informações.

* **Interface do usuário**  - Introdução à nova camada da interface do usuário que é mais ágil.

## Correções de erros {#bug-fixes}

* Em [!UICONTROL Cloud Manager] 2018.8.0, as durações da página de Atividade eram listadas em minutos e horas, mas essas informações não eram refletidas no cabeçalho da tabela.
* Em raras ocasiões, os clientes não conseguiam start no assistente de novos projetos de aplicativos.
* O rótulo do botão na caixa de diálogo do assistente para novo projeto de aplicativo estava enganoso.
* Em algumas circunstâncias, clicar no botão Detalhes na página Atividade redirecionaria para a página Visão geral.
* Algumas circunstâncias raras e inesperadas resultaram em um cartão ausente na página Visão geral.
* O ícone Ativos era exibido na página Lista do Programa para todos os clientes.
* Quando havia falhas de back-end, às vezes uma execução de pipeline parecia permanecer na etapa *Validate*.
* Em determinadas circunstâncias, a duração da descrição do programa foi mal calculada.

## Problemas conhecidos {#known-issues}

* As ramificações criadas usando o Assistente de projeto de aplicativo não podem conter traços.
* A barra lateral de notificação Adobe [!UICONTROL Experience Cloud] pode não carregar notificações de forma consistente. No entanto, as notificações estão visíveis no Adobe [!UICONTROL Experience Cloud] e, se configuradas, ainda serão enviadas por email.

