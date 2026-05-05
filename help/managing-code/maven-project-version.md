---
title: Manuseio da versão do projeto Maven
description: Saiba como o Maven lida com o controle de versão de projetos no Cloud Manager.
exl-id: a1d676e0-27cc-4b0d-8799-527c0520946a
TQID: https://experienceleague.adobe.com/bJu9-2gYrKZW78jEpaKbXiJ9b5NZEGdjICFjC4J0Dyg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 251
ht-degree: 100%

---

# Manuseio da versão do projeto Maven {#project-version}

Saiba como o Maven lida com o controle de versão de projetos no Cloud Manager.

## Como o Maven lida com versões de projetos {#how-maven}

Para implantações de preparo e produção, o Cloud Manager gera uma versão incremental e exclusiva.

Essa versão é exibida na página de detalhes de execução de pipeline e na página de atividades. Quando uma build é executada, o projeto Maven é atualizado para usar esta versão. Uma tag é criada no repositório Git com essa versão como seu nome.

Se a versão original do projeto atender a determinados critérios, a versão atualizada do projeto Maven mesclará a versão original do projeto com a versão gerada pelo Cloud Manager. No entanto, a tag sempre usará a versão gerada. Para que essa mesclagem ocorra, a versão original do projeto deve ser formada com exatamente três segmentos de versão, por exemplo, `1.0.0` ou `1.2.3`, mas não `1.0` ou `1`, e a versão original não deve terminar em `-SNAPSHOT`.

>[!NOTE]
>
>O valor da versão original do projeto deve ser definido estaticamente no elemento `<version>` do arquivo `pom.xml` de nível superior da ramificação no repositório Git.

Se a versão original atender a esses critérios, a versão gerada será anexada à versão original como um novo segmento de versão. A versão gerada também será ligeiramente modificada para incluir a classificação e o manuseio de versão corretos. Por exemplo, supondo uma versão gerada de `2019.926.121356.0000020490`:

| Versão | Versão em `pom.xml` | Comentar |
| --- | --- | --- |
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | Versão original corretamente formada |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | Versão de instantâneo, substituída |
| `1` | `2019.926.121356.0000020490` | Versão incompleta, substituída |

>[!NOTE]
>
>Se a versão original foi ou não integrada à versão inicializada pelo Cloud Manager, ela ainda poderá ser acessada como uma propriedade Maven chamada `cloudManagerOriginalVersion`.
