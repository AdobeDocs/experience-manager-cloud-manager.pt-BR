---
title: Notas da versão 2021.6.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.6.0
feature: Informações da versão
source-git-commit: c39390f34cf4ab6c9b2d5957b169c3c2cb43e6d3
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 4%

---

# Notas da versão 2021.6.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2021.6.0.

>[!NOTE]
>Consulte [Notas de versão atuais](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) para ver as notas de versão mais recentes do Cloud Manager no AEM como um Cloud Service.

## Data de lançamento {#release-date}

A data de lançamento da versão 2021.6.0 é 10 de junho de 2021.
[!UICONTROL Cloud Manager]
A próxima versão está planejada para 15 de julho de 2021.

## Novidades {#whats-new}

* Os testes de ativos e sites agora serão executados em paralelo (quando aplicável), reduzindo assim o tempo total de execução do pipeline. Esse recurso será ativado para clientes nas próximas semanas.

* As Dependências de Maven baixadas durante a etapa de build agora serão armazenadas em cache entre as execuções de pipeline. Esse recurso será ativado para clientes nas próximas semanas.

* O nome da ramificação padrão usado durante a criação do projeto e no comando push padrão por meio do gerenciamento de workflows git foi alterado para `main`.

* A experiência de edição de programa na interface do usuário foi atualizada. Consulte [Edição de um Programa](/help/using/setting-up-program.md#editing-program) para saber mais.

* A regra de qualidade `ImmutableMutableMixCheck` foi atualizada para classificar os nós `/oak:index` como imutáveis.

* As regras de qualidade `CQBP-84` e `CQBP-84--dependencies` foram consolidadas em uma única regra.

* Em algumas situações, a falha no cálculo da métrica Testes ignorados causaria falha nas execuções do pipeline.

## Correções de erros {#bug-fixes}

* Definições de nó JCR contendo uma nova linha após o nome do elemento raiz não foram analisadas corretamente.

* A API de repositórios de lista não filtra repositórios excluídos.

* Uma mensagem de erro incorreta era exibida quando um valor inválido era fornecido para a etapa de programação.

* Em alguns casos quando a execução do pipeline atingiu a etapa de implantação na produção e o usuário interrompe a execução, a mensagem de status da implantação na interface do usuário não refletia corretamente o que estava realmente acontecendo.
