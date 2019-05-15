---
title: Notas de versão de 2018.6.0
seo-title: Notas de versão do Gerenciador do AEM Cloud para 2018.6.0
description: ollow this page to get information for Cloud Manager versão 2018.6.0.
seo-description: Siga esta página para obter informações sobre a versão 2018.6.0 do Gerenciador de AEM Cloud.
uuid: 211 b 6 e 1 b -10 fb -46 b 0-b 591-44 d 5 e 44 abd 77
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas-notas
discoiquuid: 8584 f 467-3 e 61-41 ea -98 e 4-f 79 e 68 c 86469
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de versão de 2018.6.0 {#release-notes-for}

A seção a seguir descreve as Notas gerais de versão da [!UICONTROL Cloud Manager] versão 2018.6.0 e adiciona suporte para autenticação do expedidor durante implantações, notificações adicionais e melhorias de usabilidade.

## Data de lançamento {#release-date}

A Data de lançamento da [!UICONTROL Cloud Manager] versão 2018.6.0 é 9 de agosto de 2018.

## Novidades {#what-s-new}

* **CI/CD Pipeline** - Configuração do Dispatcher configurável e cache de cache em Stage e Production durante execução de CI/CD Pipeline. Consulte [Configurar seu CI/CD Pipeline](configuring-pipeline.md) para saber mais.

* **Pipeline CI/CD** - Durante a configuração do pipeline, agora é possível definir como o pipeline se comportará quando encontrar uma falha Importante em uma das passagens de qualidade. Consulte [Configurar seu CI/CD Pipeline](configuring-pipeline.md) para saber mais.

* **Pipeline CI/CD** - durante a configuração do pipeline, agora é possível selecionar se deseja que a Verificação CSE seja executada pelo CSE ou por qualquer CSE disponível. Consulte [Configurar seu CI/CD Pipeline](configuring-pipeline.md) para saber mais.

* **Pipeline CI/CD** - Quando o pipeline CI/CD chegar à etapa de aprovação comercial, uma notificação será enviada para os usuários autorizados a aprovar a implantação. Consulte [Notificações](notifications.md) para saber mais.

* **Pipeline CI/CD** - Quando o pipeline CI/CD atinge o conjunto de agendamento, uma notificação será enviada para os usuários autorizados a definir o agendamento. Consulte [Notificações](notifications.md) para saber mais.

* **Análise de qualidade de código** - Novas regras para identificar solicitações HTTP/HTTPS configuradas incorretamente. Consulte Regras de qualidade de código [personalizadas](custom-code-quality-rules.md) para saber mais.

## Correções de erros {#bug-fixes}

* Em alguns casos, o teste de desempenho não era distribuído totalmente entre vários dispatcher e instâncias de publicação.
* A navegação do cabeçalho desapareceu em janelas restritas do navegador.
* Algumas configurações de pipeline não foram desativadas enquanto o pipeline estava em execução.
* Os links para o AEM e Monitoramento na tela de Lista de programas substituíram a guia atual do navegador e abriam uma nova guia.
* Em determinadas circunstâncias, um período de aprovação longo poderia resultar em uma implantação falha.
