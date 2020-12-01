---
title: Notas da versão 2018.5.0
seo-title: Notas de versão do AEM Cloud Manager para 2018.5.0
description: Siga esta página para obter informações sobre a versão 2018.5.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2018.5.0 do AEM Cloud Manager.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 7%

---


# Notas da versão 2018.5.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2018.5.0.

## Data de lançamento {#release-date}

A data de lançamento da versão 2018.5.0 [!UICONTROL Cloud Manager] é 12 de julho de 2018.

## Novidades {#what-s-new}

* **Notificações**  de pipeline de CI/CD - os usuários agora verão  [!UICONTROL Experience Cloud] notificações de eventos de pipeline. Consulte [Notificações](notifications.md) para saber mais.

* **Implantações**  de produção agendadas - Os usuários agora podem agendar uma data ou hora, para implantações de produção. Consulte [Implantar seu código](deploying-code.md) para saber mais.

* **** Statuspage retitled to  **Atividade**.

* Informações mais específicas exibidas no home page para problemas encontrados durante a execução do pipeline.
* Melhorias na infraestrutura de teste de desempenho.

## Correções de erros {#bug-fixes}

* Em algumas condições, o perfil SonarQube incorreto foi usado, resultando em métricas de qualidade de código incorretas.
* A verificação do SonarQube CQBP-75 ignorou certas anotações do OSGi.
* Quando o pipeline CI/CD foi cancelado, o estado não era exibido de forma consistente.

## Problemas conhecidos {#known-issues}

* Os links para **AEM** e **Monitoramento** da tela de Lista do Programa substituem a guia atual do navegador e abrem para uma nova guia.

