---
title: Manuseio da versão do projeto Maven
description: Saiba como o Maven lida com o controle de versão do projeto no Cloud Manager.
exl-id: a1d676e0-27cc-4b0d-8799-527c0520946a
source-git-commit: 9312999660b324f0f9d2b44dfbf49c4813a3a6e9
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 3%

---


# Manuseio da versão do projeto Maven {#project-version}

Saiba como o Maven lida com o controle de versão do projeto no Cloud Manager.

## Como o Maven lida com versões do projeto {#how-maven}

Para implantações de armazenamento temporário e produção, o Cloud Manager gera uma versão exclusiva que aumenta.

Essa versão é vista na página de detalhes de execução do pipeline, bem como na página de atividades. Quando uma build é executada, o projeto Maven é atualizado para usar esta versão e uma tag é criada no repositório Git com essa versão como seu nome.

Se a versão original do projeto atender a determinados critérios, a versão atualizada do projeto Maven mesclará a versão original do projeto e a versão gerada pelo Cloud Manager. No entanto, a tag sempre usa a versão gerada. Para que essa mesclagem ocorra, a versão original do projeto deve ser formada com exatamente três segmentos de versão, por exemplo, `1.0.0` ou `1.2.3`, mas não `1.0` ou `1`e a versão original não deve terminar em `-SNAPSHOT`.

>[!NOTE]
>
>O valor da versão original do projeto deve ser definido estaticamente na variável `<version>` elemento do nível superior `pom.xml` na ramificação do repositório git.

Se a versão original atender a esses critérios, a versão gerada será anexada à versão original como um novo segmento de versão. A versão gerada também será ligeiramente modificada para incluir a classificação correta e o manuseio de versão. Por exemplo, assumindo uma versão gerada de `2019.926.121356.0000020490`:

| Versão | Versão em `pom.xml` | Comentar |
|---|---|---|
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | Versão original corretamente formada |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | Versão do instantâneo, substituída |
| `1` | `2019.926.121356.0000020490` | Versão incompleta, substituída |

>[!NOTE]
>
>Independentemente de a versão original ter ou não sido incorporada à versão inicializada do Cloud Manager, a versão original está disponível como uma propriedade Maven com o nome `cloudManagerOriginalVersion`.
