---
title: Notas da versão 2018.6.0
seo-title: Notas de versão do AEM Cloud Manager para 2018.6.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2018.6.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2018.6.0.
uuid: 211b6e1b-10fb-46b0-b591-44d5e44abd77
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 8584f467-3e61-41ea-98e4-f79e68c86469
feature: Informações da versão
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 4%

---


# Notas da versão 2018.6.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2018.6.0 e adiciona suporte para invalidação do dispatcher durante implantações, notificações adicionais e melhorias de usabilidade.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2018.6.0 é 9 de agosto de 2018.[!UICONTROL Cloud Manager]

## Novidades {#what-s-new}

* **Pipeline de CI/CD**  - Invalidação configurável do Dispatcher e Liberação do Cache no Estágio e na Produção durante a execução do pipeline de CI/CD. Consulte [Configure seu pipeline de CI/CD](configuring-pipeline.md) para saber mais.

* **Pipeline de CI/CD**  - Durante a configuração do pipeline, agora é possível definir como o pipeline se comportará quando encontrar uma falha importante em uma das portas de qualidade. Consulte [Configure seu pipeline de CI/CD](configuring-pipeline.md) para saber mais.

* **Pipeline de CI/CD**  - Durante a configuração do pipeline, agora é possível selecionar se você deseja que o CSE Oversight seja executado pelo CSE ou por qualquer CSE disponível. Consulte [Configure seu pipeline de CI/CD](configuring-pipeline.md) para saber mais.

* **Pipeline de CI/CD**  - Quando o pipeline de CI/CD atinge a etapa de aprovação dos negócios, uma notificação será enviada para os usuários autorizados a aprovar a implantação. Consulte [Notificações](notifications.md) para saber mais.

* **Pipeline de CI/CD**  - Quando o pipeline de CI/CD atinge o conjunto de agendamentos, uma notificação será enviada para os usuários autorizados a definir o agendamento. Consulte [Notificações](notifications.md) para saber mais.

* **Análise de qualidade do código**  - novas regras para identificar solicitações HTTP/HTTPS de saída configuradas incorretamente. Consulte [Regras de qualidade de código personalizadas](custom-code-quality-rules.md) para saber mais.

## Correções de erros {#bug-fixes}

* Em alguns casos, o teste de desempenho não foi totalmente distribuído por várias instâncias do dispatcher e de publicação.
* A navegação do cabeçalho desapareceu em janelas restritas do navegador.
* Algumas configurações de pipeline não estavam desativadas enquanto o pipeline estava em execução.
* Links para AEM e monitoramento na tela de lista Programa substituíram a guia atual do navegador e abriram uma nova guia.
* Em determinadas circunstâncias, um período de aprovação de longa duração pode resultar em uma implantação com falha.
