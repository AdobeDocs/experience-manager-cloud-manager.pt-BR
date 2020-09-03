---
title: Uso do Assistente
description: Siga esta página para saber como usar o assistente para criar um projeto de aplicativo AEM
translation-type: tm+mt
source-git-commit: 7146a41d64365c9de03d32f4fc4c33f9e366c244
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 9%

---


# Uso do Assistente {#using-wizard-to-create-an-aem-application-project}

Quando os clientes são embarcados no Cloud Manager, eles recebem um repositório git vazio. Os clientes atuais do Adobe Managed Services (AMS) (ou clientes no local AEM que estão migrando para o AMS) geralmente já terão o código do projeto em git (ou outro sistema de controle de versão) e importarão seu projeto para o repositório git do Cloud Manager. Novos clientes, no entanto, não têm projetos existentes.

Para ajudar a iniciar novos clientes, o Cloud Manager agora pode criar um projeto de AEM mínimo como ponto de partida. Esse processo se baseia no [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Siga as etapas abaixo para criar um projeto de aplicativo AEM no Cloud Manager:

1. Quando você fizer logon no Cloud Manager e a configuração básica do programa for concluída, uma chamada especial para o cartão de ação será exibida na tela **Visão geral** se o repositório estiver vazio.

   ![](assets/image2018-10-3_14-29-44.png)

1. Clique em **Criar para** abrir uma caixa de diálogo, que permite ao usuário fornecer os parâmetros exigidos pelo AEM Project Archetype. Em seu formulário padrão, a caixa de diálogo solicita dois valores:

   * **Título** - por padrão, está definido como Nome do *Programa*

   * **Novo nome** da ramificação - por padrão, isso é *principal*

   ![](assets/screen_shot_2018-10-08at55825am.png)

   A caixa de diálogo tem uma gaveta que pode ser aberta clicando na alça em direção à parte inferior da caixa de diálogo. Em seu formulário expandido, a caixa de diálogo mostra todos os parâmetros de configuração para o Archetype. Muitos desses parâmetros têm valores padrão que são gerados com base no **Título**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Por exemplo, se o **Título** for ***We.Finance***, o parâmetro de Id de artefato da base de Maven é gerado como ***com.wefinance***. Esses valores podem ser alterados, se desejado.
   >
   >
   >Por exemplo, você pode alterar do ***valor gerado com.wefinance*** para ***net.wefinance***.

1. Clique em **Criar** na etapa anterior para criar o projeto inicial usando o arquétipo e confirmando o ramo git nomeado. Quando isso estiver feito, você poderá configurar o pipeline.