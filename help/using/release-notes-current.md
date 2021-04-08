---
title: Notas da versão 2021.4.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.4.0
feature: Informações da versão
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
translation-type: tm+mt
source-git-commit: 0c33fd9f1af4c98564c9fd14a468fc3bf27744ee
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 7%

---

# Notas da versão 2021.4.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2021.4.0.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2021.4.0 é 8 de abril de 2021.
[!UICONTROL Cloud Manager]
A próxima versão está planejada para 06 de maio de 2021.

## Novidades {#whats-new}

* O tempo limite da solicitação para os usuários virtuais do teste de desempenho foi aumentado de 20 segundos para 60 segundos.

* O botão Gerenciar Git é exibido no cartão Pipelines, mesmo quando nenhum pipeline foi configurado.

* Durante a etapa de implantação da página de execução do pipeline, o usuário poderá ver as etapas de implantação concluídas e futuras, além da etapa atual na interface do usuário para o estado *Em andamento*.

* A versão do arquétipo de projeto AEM usado pelo Cloud Manager foi atualizada para a versão 27.

* A mensagem de erro ao iniciar um pipeline quando um ambiente foi excluído foi esclarecida.

* Pacotes OSGi fornecidos por projetos Eclipse agora são excluídos da regra.

## Correções de erros {#bug-fixes}

* Erros raros e transitórios que podem ocorrer na etapa Teste de ativos no pipeline de produção.

* Uma barra à direita no pipeline de produção Load Test estava causando uma falha 404.

* A verificação `Runmode` estava produzindo falsos positivos em nós que não eram pastas.