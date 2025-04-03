---
title: Uso do Assistente de novo projeto
description: Acesse esta página para saber como usar o assistente para criar um projeto de aplicativo do AEM.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: f3617eb50147f5af33282cb0f25ada7dc423d434
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 92%

---


# Usar o assistente de novo projeto {#using-the-wizard}

Quando você se integrou ao Cloud Manager como um novo cliente, recebeu um repositório Git vazio. Para ajudar você a começar, o Cloud Manager oferece um assistente para criar um projeto do AEM mínimo com base no [Arquétipo de projeto do AEM](https://github.com/adobe/aem-project-archetype) como ponto de partida.

Siga estas etapas para criar um projeto do AEM usando o assistente.

1. Faça logon no Cloud Manager, em [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com), e selecione a organização apropriada.

1. Se ainda não tiver criado, [crie seu programa](program-setup.md). Após o programa ser criado, o Cloud Manager reconhece que os repositórios ainda não estão configurados. Um cartão de chamada para ação especial é exibido na tela **Visão geral**.

   ![Criar CTA de projeto](/help/assets/image2018-10-3_14-29-44.png)

1. Clique em **Criar** para iniciar o assistente e fornecer valores importantes.

   * **Título**: o título do projeto. Por padrão, é definido como o nome do programa.
   * **Nome da nova ramificação**: a ramificação inicial dos repositórios Git. Por padrão, é `main`.

   ![Valores do projeto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. A caixa de diálogo tem uma gaveta que pode ser aberta clicando na alça em direção à parte inferior. Em sua forma expandida, a caixa de diálogo mostra todos os parâmetros de configuração do arquétipo de projeto do AEM. Esses parâmetros têm valores padrão que são gerados com base no **Título** que você já forneceu e não requerem modificação. Eles são explicados aqui para seu conhecimento.

   ![Parâmetros detalhados do arquétipo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Clique em **Criar** para criar o projeto inicial usando o arquétipo e confirmação na ramificação Git nomeada.

Agora você tem um projeto básico. É hora de configurar seus pipelines.

## Clientes já existentes ou em migração {#existing-migrating}

Se você for um cliente atual do Adobe Managed Services (AMS) ou um cliente local do AEM que está migrando para ele, provavelmente já terá o código do projeto no Git ou em outro sistema de controle de versões.

Nesses casos, você pode importar seu projeto para o repositório Git do Cloud Manager.
