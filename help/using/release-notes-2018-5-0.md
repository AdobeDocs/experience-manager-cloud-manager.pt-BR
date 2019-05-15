---
title: Notas de versão de 2018.5.0
seo-title: Notas de versão do Gerenciador do AEM Cloud para 2018.5.0
description: Siga esta página para obter informações sobre a versão 2018.5.0 do Gerenciador de nuvem.
seo-description: Siga esta página para obter informações sobre a versão 2018.5.0 do Gerenciador de AEM Cloud.
uuid: 37 f 8 b 155-6984-454 d -83 a 8-3 f 5 fb 081 be 97
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas-notas
discoiquuid: 6 d 1 e 7098-b 56 e -4172-8373-486 f 186 f 3 d 53
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de versão de 2018.5.0 {#release-notes-for}

A seção a seguir descreve as Notas gerais de versão da [!UICONTROL Cloud Manager] versão 2018.5.0.

## Data de lançamento {#release-date}

A Data de lançamento da [!UICONTROL Cloud Manager] versão 2018.5.0 é July 2 de julho de 22 18.

## Novidades {#what-s-new}

* **Notificações de pipeline CI/CD** - Os usuários agora verão [!UICONTROL Experience Cloud] notificações para eventos de pipeline. Consulte [as Notificações](notifications.md) para saber mais.

* **Implantações de produção programadas** - Os usuários podem programar uma data ou um horário para implantações de Produção. Consulte [Implantar seu código](deploying-code.md) para saber mais.

* **Página de status** retitled para **Atividade**.

* Mais informações específicas exibidas na página inicial para problemas encontrados durante a execução do pipeline.
* Melhorias na infraestrutura de teste de desempenho.

## Correções de erros {#bug-fixes}

* Em algumas condições, o perfil sonarqube incorreto foi usado, resultando em métricas de qualidade de código incorretas.
* A Verificação sonarqube CQBP -75 ignorou certas anotações osgi.
* Quando o pipeline CI/CD foi cancelado, o estado não era exibido de forma consistente.

## Problemas conhecidos {#known-issues}

* Os links para **o AEM** e **Monitoramento** na tela Lista de programas substituem a guia do navegador atual e abrem uma nova guia.

