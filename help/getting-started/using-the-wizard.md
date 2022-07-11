---
title: Usando o Assistente para Novo Projeto
description: Siga esta página para saber como usar o assistente para criar um projeto de aplicativo AEM
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# Usando o Assistente para Novo Projeto {#using-the-wizard}

Quando estiver integrado ao Cloud Manager como um novo cliente, você receberá um repositório Git vazio. Para ajudar você a começar, o Cloud Manager oferece um assistente para criar um projeto de AEM mínimo com base no [Arquétipo de projeto AEM](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) como ponto de partida.

Siga estas etapas para criar um projeto AEM usando o assistente.

1. Faça logon no Cloud Manager em [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) e selecione a organização apropriada.

1. Se ainda não tiver, [crie seu programa.](program-setup.md) Depois que o programa for criado, o Cloud Manager reconhecerá que os repositórios ainda não estão configurados e um cartão de chamada para ação especial será exibido na **Visão geral** tela.

   ![Criar CTA de projeto](/help/assets/image2018-10-3_14-29-44.png)

1. Clique em **Criar** para iniciar o assistente e fornecer valores importantes.

   * **Título** - Este é o título do projeto e, por padrão, é definido com o nome do programa.
   * **Novo Nome da Ramificação** - Essa é a ramificação inicial dos repositórios git e, por padrão, será `main`.

   ![Valores do projeto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. A caixa de diálogo tem uma gaveta que pode ser aberta clicando na alça em direção à parte inferior. Em seu formulário expandido, a caixa de diálogo mostra todos os parâmetros de configuração do arquétipo de projeto AEM. Esses parâmetros têm valores padrão que são gerados com base na variável **Título** você já forneceu e não requer modificação. Eles são explicados aqui para suas informações.

   ![Parâmetros detalhados do arquétipo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Clique em **Criar** para criar o projeto inicial usando o arquétipo e confirmar na ramificação git nomeada.

Agora você tem um projeto básico! Agora você pode configurar seus pipelines.

## Clientes existentes ou em migração {#existing-migrating}

Se você for um cliente atual do Adobe Managed Services (AMS) ou um cliente AEM local que está migrando para o, provavelmente já terá o código do projeto no git ou em outro sistema de controle de versão.

Nesses casos, você importará seu projeto para o repositório Git do Cloud Manager.
