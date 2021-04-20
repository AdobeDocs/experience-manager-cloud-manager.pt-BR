---
title: Notas da versão 2018.8.0
seo-title: Notas de versão do AEM Cloud Manager para 2018.8.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2018.8.0.
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2018.8.0.
uuid: e8aaba32-89b4-4bc5-b295-09b753252612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 9222ac3b-525e-47c1-b481-ac9d22e3d559
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 4%

---


# Notas da versão 2018.8.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2018.8.0 adiciona suporte para disparar o pipeline de CI/CD automaticamente após confirmações de git e um novo assistente para criar projetos de aplicativo no git com base no Arquétipo de projeto AEM.

## Data de lançamento {#release-date}

A Data de lançamento da versão de [!UICONTROL Cloud Manager] 2018.8.0 é 4 de outubro de 2018.

## Novidades {#what-s-new}

* **Configuração do programa**  - Novo assistente para criar um projeto de aplicativo no git usando o Arquétipo de projeto AEM

* **Pipeline de CI/CD**  - As seguintes alterações são adicionadas ao pipeline de CI/CD. Consulte [Configure seu pipeline de CI/CD](configuring-pipeline.md) para saber mais.

   * No acionador Git Changes , que inicia o pipeline de CI/CD sempre que há confirmações adicionadas à ramificação git configurada.
   * Os cartões na tela inicial agora possuem um deep link em seções específicas da página de execução do pipeline.
   * A página Atividade agora lista a ramificação específica usada para cada execução.
   * A página Atividade agora indica a duração em horas e minutos.
   * A página de execução do pipeline agora exibe a versão/nome da tag criada para a execução.
   * Apache Maven versão atualizada para 3.5.3.

* **Navegação**  - As seguintes alterações são adicionadas ao  [!UICONTROL Cloud Manager].

   * O link Recursos na navegação global navegará até o Runbook no Sharepoint.
   * O menu Ajuda foi reorganizado para incluir mais conteúdo específico de [!UICONTROL Cloud Manager].

## Correções de erros {#bug-fixes}

* Alguns detalhes na caixa de diálogo Teste de desempenho não estavam visíveis no Firefox.
* Ocasionalmente, os tempos limite entre sistemas internos faziam com que falhas de implantação fossem relatadas.
* A cor do ícone na página Atividade não estava correta para algumas execuções de pipeline bem-sucedidas.
* Em alguns casos, a caixa de diálogo Teste de desempenho listou a mesma métrica várias vezes.
* Se uma nova instância fosse adicionada após o início do pipeline de CI/CD, a implantação não seria executada na instância recém-criada.

## Problemas conhecidos {#known-issues}

* As ramificações criadas usando o Assistente de Projeto do Aplicativo não podem conter traços.
* A barra lateral de notificação [!UICONTROL Experience Cloud] pode não carregar as notificações de forma consistente. As notificações, no entanto, estão visíveis no [!UICONTROL Experience Cloud] e, se configuradas, ainda serão enviadas por email.

