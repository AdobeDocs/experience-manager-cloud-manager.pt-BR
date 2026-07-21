---
title: Anotações de verificação do GitHub
description: Saiba como o GitHub verifica PRs anotados em seus repositórios privados para fornecer um feedback útil.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 147eec6368875aabb252d759909c0309a82ef3db
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 32%

---


# Anotações de verificação do GitHub {#github-annotations}

Saiba como o GitHub verifica as PRs de anotação de seus repositórios privados para fornecer feedback.

## Visão geral {#overview}

Se você usa [repositórios privados](private-repositories.md) para seu programa Cloud Manager, o verifica no GitHub é executado automaticamente para cada solicitação de pull. Essas verificações são anotadas com informações para ajudar você a identificar problemas com seu código o mais rápido possível.

![Exemplo de anotações de verificação do GitHub](assets/github-check-annotations.png)

Os problemas de [qualidade do código](/help/using/code-quality-testing.md) detectados pelo [SonarQube](/help/using/custom-code-quality-rules.md) estão claramente listados.

![Exemplo de anotação de problema de código](assets/github-check-annotations-example.png)

A linha exata de código com o problema é fornecida e você pode selecioná-la para exibir o código relevante. Essas anotações são fornecidas para todos os problemas de código, não apenas aqueles na solicitação de pull.

![Exemplo de anotação de problema de código](assets/github-check-annotations-example-code.png)

Todas as linhas anotadas são agregadas na guia **Arquivos alterados** na solicitação de pull do GitHub. As anotações de arquivos não alterados na solicitação de pull aparecem em uma seção separada.

![Exemplo de anotações na guia de arquivos alterados](assets/github-check-annotations-files-changed.png)

## Pipelines da qualidade de código {#code-quality-pipelines}

Os resultados [Qualidade do código](/help/using/code-quality-testing.md) também estão visíveis no pipeline, que o Cloud Manager aciona automaticamente, na parte inferior da guia **Verificações**. Também é acessível por meio dos **Detalhes** da verificação da solicitação de pull.

![Exemplo de anotações](assets/github-check-annotations-code-quality.png)

![Exemplo de anotações](assets/github-check-annotations-code-quality-2.png)

Você também pode visualizar os problemas como um arquivo CSV. Você pode acessar essas informações [vendo os detalhes da execução do pipeline no Cloud Manager](/help/using/managing-pipelines.md).
