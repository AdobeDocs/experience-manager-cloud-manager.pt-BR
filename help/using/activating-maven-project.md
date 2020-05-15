---
title: Manuseio da versão do projeto Maven
seo-title: Manuseio da versão do projeto Maven
description: Saiba mais sobre o Maven Project Version Handling.
seo-description: Siga esta página para saber mais sobre o Maven Project Version Handling.
translation-type: tm+mt
source-git-commit: e2187565e7f06d64841eb2af9b4b1a56feb5ebe4
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 7%

---


# Manuseio da versão do projeto Maven {#project-version}

## Understanding Maven Project Version Handling {#understanding-project-version}

Para implantações de estágio e de produção, o Cloud Manager gera uma versão única, que aumenta.

Esta versão é vista na página de detalhes da execução do pipeline, bem como na página de atividade. Quando uma compilação é executada, o projeto Maven é atualizado para usar esta versão e uma tag é criada no repositório git com essa versão como seu nome.

Se a versão original do projeto atender a determinados critérios, a versão atualizada do projeto Maven mesclará a versão original do projeto e a versão gerada pelo Gerenciador de nuvem. Entretanto, a tag sempre usa a versão gerada. Para que essa união ocorra, a versão original do projeto deve ser formada com exatamente três segmentos de versão, por exemplo, 1.0.0 ou 1.2.3, mas não 1.0 ou 1, e a versão original não deve terminar em -SNAPSHOT.

Se a versão original atender a esses critérios, a versão gerada será anexada à versão original como um novo segmento de versão. A versão gerada também será ligeiramente modificada para incluir a classificação correta e o manuseio de versão. Por exemplo, assumindo uma versão gerada de 2019.926.121356.000020490:

| **Versão** | **versão em pom.xml** | **Comentário** |
|---|---|---|
| 1.0.0 | 1.0.0.2019_0926_121356_0000020490 | Versão original corretamente formada |
| 1.0.0-SNAPSHOT | 2019.926.121356.0000020490 | Versão do instantâneo, substituída |
| 1 | 2019.926.121356.0000020490 | Versão incompleta, substituída |

>[!NOTE]
>
>Independentemente de a versão original ter sido incorporada ou não à versão inicializada do Gerenciador de nuvem, a versão original está disponível como uma propriedade Maven com o nome *cloudManagerOriginalVersion.*
