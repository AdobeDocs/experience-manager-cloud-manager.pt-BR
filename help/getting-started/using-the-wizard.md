---
title: Usando o assistente para novo projeto
description: Siga esta página para saber como usar o assistente para criar um projeto de aplicativo do AEM
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 100%

---


# Usando o assistente para novo projeto {#using-the-wizard}

Quando estiver integrado ao Cloud Manager como um novo cliente, você receberá um repositório Git vazio. Para ajudar você a começar, o Cloud Manager oferece um assistente para criar um projeto do AEM mínimo com base no [Arquétipo de projeto do AEM](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) como ponto de partida.

Siga estas etapas para criar um projeto do AEM usando o assistente.

1. Faça logon no Cloud Manager, em [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com), e selecione a organização apropriada.

1. Se ainda não tiver feito, [crie seu programa.](program-setup.md) Depois que o programa for criado, o Cloud Manager reconhecerá que os repositórios ainda não estão configurados e um cartão de chamada para ação especial será exibido na tela **Visão geral**.

   ![Criar CTA de projeto](/help/assets/image2018-10-3_14-29-44.png)

1. Clique em **Criar** para iniciar o assistente e fornecer valores importantes.

   * **Título** - Este é o título do projeto e, por padrão, é definido como o nome do programa.
   * **Nome da nova ramificação** - Essa é a ramificação inicial dos repositórios Git e, por padrão, será `main`.

   ![Valores do projeto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. A caixa de diálogo tem uma gaveta que pode ser aberta clicando na alça em direção à parte inferior. Em sua forma expandida, a caixa de diálogo mostra todos os parâmetros de configuração do arquétipo de projeto do AEM. Esses parâmetros têm valores padrão que são gerados com base no **Título** que você já forneceu e não requerem modificação. Eles são explicados aqui para seu conhecimento.

   ![Parâmetros detalhados do arquétipo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Clique em **Criar** para criar o projeto inicial usando o arquétipo e confirmar na ramificação Git nomeada.

Agora você tem um projeto básico! Agora você pode configurar seus pipelines.

## Clientes existentes ou em migração {#existing-migrating}

Se você for um cliente atual do Adobe Managed Services (AMS) ou um cliente local do AEM que está migrando para ele, provavelmente já terá o código do projeto no Git ou em outro sistema de controle de versões.

Nesses casos, você importará seu projeto para o repositório Git do Cloud Manager.
