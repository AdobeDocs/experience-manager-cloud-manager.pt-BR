---
title: Configuração de verificação do GitHub para repositórios privados
description: Saiba como controlar os pipelines criados automaticamente para validar cada solicitação de pull para um repositório privado.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 39%

---

# Verificar configuração do GitHub para repositórios privados {#github-check-config}

Saiba como controlar os pipelines criados automaticamente para validar cada solicitação de pull para um repositório privado.

## Configuração de verificações do GitHub {#configuration}

Ao usar [repositórios privados](private-repositories.md#using), um [pipeline de qualidade de código de pilha completa](/help/overview/ci-cd-pipelines.md) é criado automaticamente. Esse pipeline é iniciado a cada atualização de solicitação de pull.

Você pode controlar essas verificações criando um arquivo `.cloudmanager/pr_pipelines.yml` na ramificação padrão do repositório privado.

```yaml
github:
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
| `shouldDeletePreviousComment` | `true` ou `false` | `false` | Se deseja manter somente o último comentário com os resultados da verificação de código nesta solicitação de pull do GitHub ou manter todos. |
| `type` | `CI_CD` | n/a | Define o comportamento de um pipeline de CI/CD. |
| `template.programID` | Número inteiro | Nenhuma variável de pipeline é reutilizada | Você pode reutilizar as [variáveis de pipeline](/help/getting-started/build-environment.md#pipeline-variables) definidas em um pipeline existente, que cada PR cria automaticamente. |
| `template.pipelineID` | Número inteiro | Nenhuma variável de pipeline é reutilizada | Você pode reutilizar as [variáveis de pipeline](/help/getting-started/build-environment.md#pipeline-variables) definidas em um pipeline existente, que cada PR cria automaticamente. |
| `namePrefix` | String | `Full Stack Code Quality Pipeline for PR` | Usado para definir o nome do pipeline que é criado automaticamente. |
| `importantMetricsFailureBehavior` | `CONTINUE` ou `FAIL` ou `PAUSE` | `CONTINUE` | Define o comportamento de métrica importante do pipeline <br>`CONTINUE` = Se uma métrica importante falhar, o pipeline se move automaticamente <br>`FAIL` = O pipeline termina com um status FALHA se uma métrica importante falhar <br>`PAUSE` = A etapa de verificação de código recebe um status DE ESPERA quando uma métrica importante falha e deve ser retomada manualmente. |
