---
title: Notas de versão para 2018.5.0
seo-title: Notas de versão do AEM Cloud Manager para 2018.5.0
description: Siga esta página para obter informações sobre a versão 2018.5.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2018.5.0 do AEM Cloud Manager.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas de versão
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b

---


# Notas de versão para 2018.5.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2018.5.0.

## Data de lançamento {#release-date}

The Release Date for  Version 2018.5.0 is July 12, 2018.[!UICONTROL Cloud Manager]

## Novidades {#what-s-new}

* **CI/CD Pipeline Notifications** - Users will now see [!UICONTROL Experience Cloud] notifications for pipeline events. Please refer to the Notifications to learn more.[](notifications.md)

* **Implantações** de produção agendadas - os usuários agora podem agendar uma data ou hora para implantações de produção. Please refer to Deploy Your Code to learn more.[](deploying-code.md)

* **Status page retitled to Activity.******

* Informações mais específicas exibidas na página inicial para problemas encontrados durante a execução do pipeline.
* Melhorias na infraestrutura de teste de desempenho.

## Correções de erros {#bug-fixes}

* Em algumas condições, o perfil SonarQube incorreto foi usado, resultando em métricas de qualidade de código incorretas.
* A verificação do SonarQube CQBP-75 ignorou certas anotações OSGi.
* Quando o pipeline CI/CD foi cancelado, o estado não era exibido de forma consistente.

## Problemas conhecidos {#known-issues}

* Links to AEM and Monitoring from Program List screen both replace the current browser tab and opens to a new tab.********

