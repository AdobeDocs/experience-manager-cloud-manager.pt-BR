---
title: Verificações de solicitação de pull para repositórios privados
description: Saiba como controlar os pipelines criados automaticamente para validar cada solicitação de pull para um repositório privado.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 1ae6792f8bc628c3530a63004c3d38f215c72778
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 92%

---

# Verificações de solicitação de pull para repositórios privados {#github-check-config}

<!--OLD TITLE THAT I THOUGHT WAS BETTER Check configuration for private repositories -->

Saiba como controlar os pipelines criados automaticamente para validar cada solicitação de pull para um repositório privado.

## Configuração de verificações de repositório privado {#configuration}

Ao usar [repositórios privados](private-repositories.md#using), um [pipeline de qualidade de código de pilha completa](/help/overview/ci-cd-pipelines.md) será criado automaticamente. Esse pipeline é iniciado a cada atualização de solicitação de pull.

Você pode controlar essas verificações criando um arquivo `.cloudmanager/pr_pipelines.yml` na ramificação padrão do repositório privado.

```yaml
pullRequest:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR
    importantMetricsFailureBehavior: CONTINUE
```

| Parâmetro | Valores possíveis | Padrão | Descrição |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` ou `false` | `false` | Seja para manter apenas o último comentário com os resultados da verificação de código nesta solicitação de pull do GitHub ou para manter todos. |
| `type` | `CI_CD` | n/d | Define o comportamento de um pipeline de CI/CD. |
| `template.programID` | Número inteiro | Nenhuma variável de pipeline é reutilizada | Você pode reutilizar as [variáveis de pipeline](/help/getting-started/build-environment.md#pipeline-variables) definidas em um pipeline já existente, que cada PR cria automaticamente. |
| `template.pipelineID` | Número inteiro | Nenhuma variável de pipeline é reutilizada | Você pode reutilizar as [variáveis de pipeline](/help/getting-started/build-environment.md#pipeline-variables) definidas em um pipeline já existente, que cada PR cria automaticamente. |
| `namePrefix` | String | `Full Stack Code Quality Pipeline for PR` | Usado para definir o nome do pipeline criado automaticamente. |
| `importantMetricsFailureBehavior` | `CONTINUE` ou `FAIL` ou `PAUSE` | `CONTINUE` | Define o comportamento de métricas importantes do pipeline<br>`CONTINUE` = Se uma métrica importante falha, o pipeline avança automaticamente<br>`FAIL` = O pipeline termina com um status FAILED se uma métrica importante falha<br>`PAUSE` = A etapa de verificação de código recebe um status WAITING quando uma métrica importante falha e deve ser retomada manualmente. |
