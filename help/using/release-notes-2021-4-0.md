---
title: Notas da versão 2021.4.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.4.0
feature: Release Information
source-git-commit: 09dd8fe608d95cd9dbc95129cf86b9693c2839b5
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 6%

---

# Notas da versão 2021.4.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais de [!UICONTROL Cloud Manager] Versão 2021.4.0.

## Data de lançamento {#release-date}

A data de lançamento para [!UICONTROL Cloud Manager] A versão 2021.4.0 é 8 de abril de 2021.

## Novidades {#whats-new}

* O tempo limite da solicitação para os usuários virtuais do teste de desempenho foi aumentado de 20 segundos para 60 segundos.

* O botão Gerenciar Git é exibido no cartão Pipelines, mesmo quando nenhum pipeline foi configurado.

* Durante a etapa de implantação da página de execução do pipeline, o usuário poderá ver as etapas de implantação concluídas e futuras, além da etapa atual na interface do usuário para *Em Andamento* estado.

* A versão do arquétipo de projeto AEM usado pelo Cloud Manager foi atualizada para a versão 27.

* A mensagem de erro ao iniciar um pipeline quando um ambiente foi excluído foi esclarecida.

* Pacotes OSGi fornecidos por projetos Eclipse agora são excluídos da regra `CQBP-84--dependencies`.

## Correções de erros {#bug-fixes}

* Erros raros e transitórios que podem ocorrer em *Teste de ativos* no pipeline de produção.

* Uma barra à direita no pipeline de produção Load Test estava causando uma falha 404.

* O `Runmode` check estava produzindo falsos positivos em nós que não eram pastas.