---
title: Notas da versão 2018.5.0
seo-title: Notas de versão do AEM Cloud Manager para 2018.5.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2018.5.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2018.5.0.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
feature: Release Information
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 8%

---


# Notas da versão 2018.5.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2018.5.0.

## Data de lançamento {#release-date}

A data de lançamento da versão [!UICONTROL Cloud Manager] 2018.5.0 é 12 de julho de 2018.

## Novidades {#what-s-new}

* **Notificações de pipeline de CI/CD**  - Os usuários agora verão  [!UICONTROL Experience Cloud] as notificações para eventos de pipeline. Consulte as [Notificações](notifications.md) para saber mais.

* **Implantações programadas de produção**  - Os usuários agora podem programar uma data ou hora para implantações de Produção. Consulte [Implantar o código](deploying-code.md) para saber mais.

* **** Página de status com direito à  **Atividade**.

* Informações mais específicas exibidas na home page para problemas encontrados durante a execução do pipeline.
* Melhorias na infraestrutura de teste de desempenho.

## Correções de erros {#bug-fixes}

* Sob algumas condições, o perfil SonarQube incorreto foi usado, resultando em métricas de qualidade de código incorretas.
* SonarQube check CQBP-75 ignorou certas anotações OSGi.
* Quando o pipeline de CI/CD foi cancelado, o estado não era exibido de forma consistente.

## Problemas conhecidos {#known-issues}

* Links para **AEM** e **Monitoring** da tela Lista de programas substituem a guia atual do navegador e são abertos em uma nova guia.

