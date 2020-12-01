---
title: Notas da versão 2018.6.0
seo-title: Notas de versão do AEM Cloud Manager para 2018.6.0
description: Siga esta página para obter informações sobre a versão 2018.6.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2018.6.0 do AEM Cloud Manager.
uuid: 211b6e1b-10fb-46b0-b591-44d5e44abd77
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 8584f467-3e61-41ea-98e4-f79e68c86469
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 3%

---


# Notas da versão 2018.6.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2018.6.0 e adiciona suporte para a invalidação do dispatcher durante implantações, notificações adicionais e melhorias de usabilidade.

## Data de lançamento {#release-date}

A data de lançamento da versão 2018.6.0 [!UICONTROL Cloud Manager] é 9 de agosto de 2018.

## Novidades {#what-s-new}

* **Pipeline**  CI/CD - Invalidação do Dispatcher Configurável e Descarga do Cache no Estágio e na Produção durante a execução do Pipeline CI/CD. Consulte [Configure seu pipeline CI/CD](configuring-pipeline.md) para saber mais.

* **Pipeline**  CI/CD - Durante a configuração do pipeline, agora é possível definir como o pipeline se comportará quando encontrar uma falha importante em uma das portas de qualidade. Consulte [Configure seu pipeline CI/CD](configuring-pipeline.md) para saber mais.

* **Pipeline**  CI/CD - Durante a configuração do pipeline, agora é possível selecionar se você deseja que a CSE Oversight seja executada pelo CSE ou qualquer CSE disponível. Consulte [Configure seu pipeline CI/CD](configuring-pipeline.md) para saber mais.

* **Pipeline**  CI/CD - Quando o pipeline CI/CD atingir a etapa de aprovação da empresa, uma notificação será enviada aos usuários autorizados a aprovar a implantação. Consulte [Notificações](notifications.md) para saber mais.

* **Pipeline**  CI/CD - Quando o pipeline CI/CD atingir o agendamento definido, uma notificação será enviada aos usuários autorizados a definir o agendamento. Consulte [Notificações](notifications.md) para saber mais.

* **Análise**  de qualidade de código - novas regras para identificar solicitações HTTP/HTTPS de saída configuradas incorretamente. Consulte [Regras de qualidade de código personalizadas](custom-code-quality-rules.md) para saber mais.

## Correções de erros {#bug-fixes}

* Em alguns casos, o teste de desempenho não foi totalmente distribuído por várias instâncias de despacho e publicação.
* A navegação do cabeçalho desapareceu em janelas estreitas do navegador.
* Algumas configurações de pipeline não foram desativadas enquanto o pipeline estava em execução.
* Os links para AEM e Monitoramento na tela de lista do Programa substituíram a guia atual do navegador e abriram uma nova guia.
* Em determinadas circunstâncias, um período de aprovação de longa duração pode resultar em uma implantação com falha.
