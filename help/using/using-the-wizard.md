---
title: Usar o Assistente
description: Siga esta página para saber como usar o assistente para criar um projeto de aplicativo AEM
feature: Getting Started
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 10%

---


# Usar o Assistente {#using-wizard-to-create-an-aem-application-project}

Quando os clientes são integrados ao Cloud Manager, eles recebem um repositório Git vazio. Os clientes atuais do Adobe Managed Services (AMS) (ou clientes no local AEM que estão migrando para o AMS) geralmente já têm o código do projeto no git (ou em outro sistema de controle de versão) e importarão seu projeto para o repositório de git do Cloud Manager. Os novos clientes, no entanto, não têm projetos existentes.

Para ajudar a iniciar novos clientes, o Cloud Manager agora pode criar um projeto de AEM mínimo como ponto de partida. Esse processo é baseado no [**AEM Arquétipo de Projeto**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Siga as etapas abaixo para criar um projeto de aplicativo AEM no Cloud Manager:

1. Quando você fizer logon no Cloud Manager e a configuração básica do programa for concluída, uma chamada especial para o cartão de ação será exibida na tela **Visão geral** se o repositório estiver vazio.

   ![](assets/image2018-10-3_14-29-44.png)

1. Clique em **Criar para** para abrir uma caixa de diálogo, que permite que o usuário forneça os parâmetros exigidos pelo Arquétipo de projeto AEM. Em seu formulário padrão, a caixa de diálogo solicita dois valores:

   * **Título**  - por padrão, isso é definido como Nome do  *programa*

   * **Novo nome da ramificação**  - por padrão, isso é  *principal*

   ![](assets/screen_shot_2018-10-08at55825am.png)

   A caixa de diálogo tem uma gaveta que pode ser aberta clicando na alça em direção à parte inferior da caixa de diálogo. Em seu formulário expandido, a caixa de diálogo mostra todos os parâmetros de configuração do Arquétipo. Muitos desses parâmetros têm valores padrão que são gerados com base no **Title**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Por exemplo, se o **Title** for ***We.Finance***, o parâmetro Base Maven Artifact Id será gerado como ***com.wefinance***. Esses valores podem ser alterados, se desejado.
   >
   >
   >Por exemplo, você pode alterar do ***valor com.wefinance*** gerado para ***net.wefinance***.

1. Clique em **Create** na etapa anterior para criar o projeto inicial usando o arquétipo e confirmando na ramificação git nomeada. Feito isso, você pode configurar o pipeline.