---
title: Notas de versão de 2018.8.0
seo-title: Notas de versão do Gerenciador do AEM Cloud para 2018.8.0
description: Siga esta página para obter informações sobre a versão 2018.8.0 do Gerenciador de nuvem.
seo-description: Siga esta página para obter informações sobre a versão 2018.8.0 do Gerenciador de AEM Cloud.
uuid: e 8 acast 32-89 b 4-4 bc 5-b 295-09 b 753252612
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas-notas
discoiquuid: 9222 ac 3 b -525 e -47 c 1-b 481-ac 9 d 22 e 3 d 559
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de versão de 2018.8.0 {#release-notes-for}

A [!UICONTROL Cloud Manager] versão 2018.8.0 adiciona suporte para acionar o pipeline CI/CD automaticamente após vírgula e um novo assistente para criar projetos de aplicativos no git com base no Arquetype do projeto do AEM.

## Data de lançamento {#release-date}

A Data de lançamento da [!UICONTROL Cloud Manager] versão 2018.8.0 é October 4 de outubro de 24 18.

## Novidades {#what-s-new}

* **Configuração** de programa - Novo assistente para criar um projeto de aplicativo no git usando o Arquivador de projetos do AEM, consulte [Criar um projeto do AEM Application](create-an-application-project.md) para saber mais.

* **Pipeline CI/CD** - as seguintes alterações são adicionadas a CI/CD Pipeline. Consulte [Configurar seu CI/CD Pipeline](configuring-pipeline.md) para saber mais.

   * No acionador Alterações Git, que inicia o pipeline CI/CD sempre que há vírgulas adicionadas ao ramo de git configurado.
   * Cartões na tela inicial agora são deep link em seções específicas da página de execução do pipeline.
   * A página de atividade agora lista o ramo específico usado para cada execução.
   * A página de atividade agora indica a duração em horas e minutos.
   * A página de execução do pipeline agora exibe o nome da versão/tag criada para a execução.
   * Versão do Apache Maven atualizada para 3.5.3.

* **Navegação** - as seguintes alterações são adicionadas ao [!UICONTROL Cloud Manager].

   * O link de recursos na navegação global navegará até o Runbook no Sharepoint.
   * O menu Ajuda foi reorganizado para incluir mais [!UICONTROL Cloud Manager]conteúdo específico.

## Correções de erros {#bug-fixes}

* Alguns detalhes na caixa de diálogo Teste de desempenho não estavam visíveis no Firefox.
* Tempos limite entre sistemas internos fazem com que as falhas de implantação sejam relatadas.
* A cor de ícone na página Atividade não estava correta para algumas execuções de pipeline bem-sucedidas.
* Em alguns casos, a caixa de diálogo Teste de desempenho listou a mesma métrica várias vezes.
* Se uma nova instância foi adicionada após o início do pipeline CI/CD, a implantação não será executada na instância criada recentemente.

## Problemas conhecidos {#known-issues}

* As ramificações criadas usando o Assistente de projeto do aplicativo não podem conter traços.
* A barra lateral [!UICONTROL Experience Cloud] de notificação pode não carregar notificações consistentemente. No entanto, as notificações estão visíveis no [!UICONTROL Experience Cloud] e, se configuradas, ainda serão enviadas por email.

