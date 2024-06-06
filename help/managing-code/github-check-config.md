---
title: Verificação de configuração do GitHub para repositórios privados
description: Saiba como controlar os pipelines criados automaticamente para validar cada solicitação de pull para um repositório privado.
source-git-commit: 85c1e22609dc5646d3de0ccc71e9423d4243e13a
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 7%

---


# Verificação de configuração do GitHub para repositórios privados {#github-check-config}

Saiba como controlar os pipelines criados automaticamente para validar cada solicitação de pull para um repositório privado.

## Configuração de verificações do GitHub {#configuration}

Ao usar [repositórios privados,](private-repositories.md#using) a [pipeline de qualidade do código de pilha completa](/help/overview/ci-cd-pipelines.md) será criado automaticamente. Esse pipeline é iniciado a cada atualização de solicitação de “pull”.

Você pode controlar essas verificações criando uma `.cloudmanager/pr_pipelines.yml` arquivo na ramificação padrão do repositório privado.

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
|---|---|---|---|
| `shouldDeletePreviousComment` | `true` ou `false` | `false` | Se deve manter somente o último comentário com os resultados da verificação de código nesta solicitação de pull do GitHub ou manter todos |
| `type` | `CI_CD` | n/a | Define o comportamento de um pipeline de CI/CD |
| `template.programID` | Número inteiro | Nenhuma variável de pipeline é reutilizada | Pode ser usado para reutilizar a variável [variáveis de pipeline](/help/getting-started/build-environment.md#pipeline-variables) que são definidos em um dos pipelines existentes que são criados automaticamente por cada PR. |
| `template.pipelineID` | Número inteiro | Nenhuma variável de pipeline é reutilizada | Pode ser usado para reutilizar a variável [variáveis de pipeline](/help/getting-started/build-environment.md#pipeline-variables) que são definidos em um dos pipelines existentes que são criados automaticamente por cada PR. |
| `namePrefix` | String | `Full Stack Code Quality Pipeline for PR` | Usado para definir o nome do pipeline que é criado automaticamente |
| `importantMetricsFailureBehavior` | `CONTINUE` ou `FAIL` ou `PAUSE` | `CONTINUE` | Define o comportamento de métrica importante do pipeline<br>`CONTINUE` = Se uma métrica importante falhar, o pipeline avançará automaticamente<br>`FAIL` = O pipeline terminará com um status FALHA se uma métrica importante falhar<br>`PAUSE` = A etapa de verificação de código receberá um status WAITING quando uma métrica importante falhar e deverá ser retomada manualmente |
