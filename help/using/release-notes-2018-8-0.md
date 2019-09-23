---
title: Notas de versão para 2018.8.0
seo-title: Notas de versão do AEM Cloud Manager para 2018.8.0
description: Siga esta página para obter informações sobre a versão 2018.8.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2018.8.0 do AEM Cloud Manager.
uuid: e8aaba32-89b4-4bc5-b295-09b753252612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas de versão
discoiquuid: 9222ac3b-525e-47c1-b481-ac9d22e3d559
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b

---


# Notas de versão para 2018.8.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2018.8.0 adiciona suporte para acionar o pipeline de CI/CD automaticamente após confirmações de git e um novo assistente para criar projetos de aplicativos no git com base no AEM Project Archetype.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2018.8.0 é 4 de outubro de 2018.

## Novidades {#what-s-new}

* **Configuração** do programa - Novo assistente para criar um projeto de aplicativo no git usando o AEM Project Archetype Consulte [Criar um projeto](create-an-application-project.md) de aplicativo AEM para saber mais.

* **Pipeline** CI/CD - As seguintes alterações são adicionadas ao pipeline CI/CD. Consulte [Configure seu pipeline](configuring-pipeline.md) CI/CD para saber mais.

   * On Git Changes (Mudanças no Git), que inicia o pipeline de CI/CD sempre que há confirmações adicionadas ao ramo git configurado.
   * Os cartões na tela inicial agora se vinculam profundamente a seções específicas da página de execução de pipeline.
   * A página Atividade agora lista o ramo específico usado para cada execução.
   * A página de atividade agora indica a duração em horas e minutos.
   * A página de execução do pipeline agora exibe o nome da versão/tag criado para a execução.
   * Apache Maven versão atualizada para 3.5.3.

* **Navegação** - as seguintes alterações são adicionadas ao [!UICONTROL Cloud Manager].

   * O link Recursos na navegação global navegará até o Runbook no Sharepoint.
   * O menu Ajuda foi reorganizado para incluir conteúdo mais [!UICONTROL Cloud Manager]específico.

## Correções de erros {#bug-fixes}

* Alguns detalhes na caixa de diálogo Teste de desempenho não estavam visíveis no Firefox.
* Os tempos limite entre sistemas internos ocasionalmente causariam falhas de implantação a serem relatadas.
* A cor do ícone na página Atividade não estava correta para algumas execuções bem-sucedidas do pipeline.
* Em alguns casos, a caixa de diálogo Teste de desempenho listou a mesma métrica várias vezes.
* Se uma nova instância fosse adicionada após o pipeline de CI/CD ter sido iniciado, a implantação não seria executada na instância recém-criada.

## Problemas conhecidos {#known-issues}

* As ramificações criadas usando o Assistente de projeto de aplicativo não podem conter traços.
* A barra lateral de [!UICONTROL Experience Cloud] notificação pode não carregar as notificações de forma consistente. No entanto, as notificações estão visíveis no e, se configuradas, ainda serão enviadas por email. [!UICONTROL Experience Cloud]

