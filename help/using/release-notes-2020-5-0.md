---
title: Notas da versão 2020.5.0
seo-title: Notas de versão do AEM Cloud Manager para 2020.5.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2020.5.0
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2020.5.0
feature: Informações da versão
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 67%

---

# Notas da versão 2020.5.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2020.5.0.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2020.5.0 é 7 de maio de 2020.[!UICONTROL Cloud Manager]

## Novidades {#whats-new}

* Seis regras adicionais de qualidade de código foram adicionadas para ajudar os clientes a identificar possíveis problemas ao planejar uma migração para o Cloud Service.

* Foi adicionada uma nova métrica *Compatibilidade com o Cloud Service* para resumir o número de problemas relacionados à compatibilidade.

* O desempenho da página Atividade e da API de Lista de execuções de pipeline foi aprimorado.

* O log de qualidade do código agora contém rastreamentos completos de pilha para exceções.

## Correções de erros {#bug-fixes}

* Um cartão enganoso era exibido na página de visão geral enquanto o pipeline de produção estava em execução.

* A regra de qualidade de código *DontImplementOrExtendProviderTypesPomCheck* pode, às vezes, produzir uma Exceção de ponteiro nulo.

* Alguns links de documentação da página de visão geral não funcionavam corretamente.

* Determinados cartões na página de visão geral não exibiam os nomes de entidades corretamente.

* Certas configurações de topologia faziam com que a etapa de teste de desempenho gerasse um erro, em vez de relatar métricas ausentes.

