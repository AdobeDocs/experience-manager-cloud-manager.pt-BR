---
title: Uso do Assistente de novo projeto
description: Acesse esta página para saber como usar o assistente para criar um projeto de aplicativo do AEM.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
TQID: https://experienceleague.adobe.com/zoiHL1lNC2XN-T9g0dh3pQyL4Yw3uYgFpHs8d6hkj3M
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 317
ht-degree: 54%

---

# Usar o assistente de novo projeto {#using-the-wizard}

Quando estiver integrado ao Cloud Manager como um novo cliente, você receberá um repositório Git vazio. Para ajudar você a começar, a Cloud Manager oferece um assistente para criar um projeto mínimo do AEM com base no [Arquétipo de Projetos AEM](https://github.com/adobe/aem-project-archetype) como ponto de partida.

**Para usar o assistente de novo projeto:**

1. Faça logon no Cloud Manager, em [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com), e selecione a organização apropriada.

1. Se ainda não tiver criado, [crie seu programa](program-setup.md). Quando o programa é criado, o Cloud Manager detecta que o repositório não está configurado. Um cartão de prompt especial é exibido na tela **Visão geral**.

   ![Criar CTA de projeto](/help/assets/image2018-10-3_14-29-44.png)

1. Clique em **Criar** para iniciar o assistente e fornecer valores importantes.

   * **Título**: o título do projeto. Por padrão, é definido como o nome do programa.
   * **Nome da nova ramificação** - A ramificação inicial do repositório Git. Por padrão, é `main`.

   ![Valores do projeto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. A caixa de diálogo tem uma seção que pode ser exibida clicando no ícone próximo à parte inferior. Em sua forma expandida, a caixa de diálogo mostra todos os parâmetros de configuração do arquétipo de projeto do AEM. Esses parâmetros têm valores padrão que são gerados com base no **Título** que você já forneceu e não requerem modificação. Eles são explicados aqui para seu conhecimento.

   ![Parâmetros detalhados do arquétipo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Clique em **Criar** para criar o projeto inicial usando o arquétipo e confirmação na ramificação Git nomeada.

Agora você tem um projeto básico. Agora você pode configurar seus pipelines.

## Clientes já existentes ou em migração {#existing-migrating}

Se você for um cliente atual do Adobe Managed Services (AMS) ou um cliente local do AEM que está migrando, já terá o código do projeto no Git ou em outro sistema de controle de versão.

Nesses casos, você pode importar seu projeto para o repositório Git do Cloud Manager.
